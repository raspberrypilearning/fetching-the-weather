## Finding the distance between two points on the Earth

The next part is a little technical. You need to be able to find the distance between two points on the Earth, given their longitudes and latitudes. This will allow you to find the closest Weather Station to you.

If you're not particularly interested in how this works, then rather than write the code, you can download the file you need from [here](https://raw.githubusercontent.com/raspberrypilearning/fetching-the-weather/master/code/haversine.py). Just make sure it's saved as `haversine.py` and stored in the same directory as the rest of your code.

As discussed earlier, we use longitude and latitude to work out the exact position of places on the Earth. Finding distances between these points is quite tricky, as the distance is over the surface of a sphere, and therefore not in a straight line. To do this calculation, you need a clever bit of maths called the [haversine formula](https://en.wikipedia.org/wiki/Haversine_formula).

Without getting too technical, the haversine formula can provide the distance between two points on a sphere using longitudes and latitudes.

- Create a new program by clicking on `File` > `New File` in the Python script. 

- Click on `File` > `Save As` and call your file `haversine.py`.

- To begin with, you're going to need a few functions from the `maths` library. Start off your file by importing the following:

    ``` python
    from math import radians, cos, sin, asin, sqrt
    ```

- Now you can define a new function, which we'll call `haversine`. It's going to take 4 arguments, which will be the longitude and latitude of the two points whose distance we need to find.

    ``` python
    def haversine(lon1, lat1, lon2, lat2):
    ```
- Most mathematical formulae require us to work in [radians](http://www.bbc.co.uk/bitesize/higher/maths/trigonometry/radian_and_equations/revision/1/) rather than degrees when dealing with angles, so the first thing to do is to convert each of the latitudes and longitudes passed into the function as arguments into radians.

    ``` python
    def haversine(lon1, lat1, lon2, lat2):
        #convert degrees to radians
        lon1 = radians(lon1)
        lat1 = radians(lat1)
        lon2 = radians(lon2)
        lat2 = radians(lat2)
    ```
    
- Now we want to find the difference between the two longitudes and latitudes, so add this into your function:

    ``` python
        dlon = lon2 - lon1 
        dlat = lat2 - lat1 
    ```

- Now comes the tricky bit. If you want to know more about the haversine formula then you can have a read of the Wikipedia article linked above. Otherwise, you can just take it at face value that the following lines of code will calculate the distance between the two points:

    ``` python
        a = sin(dlat/2)**2 + cos(lat1) * cos(lat2) * sin(dlon/2)**2
        distance = 2 * asin(sqrt(a)) * 6371 #6371 is the radius of the Earth
        return distance
    ```

The number `6371` in the code above is the radius of the Earth

- Save your file and run your program to test it.

- In the Python shell type the following:

    ``` python
    haversine(74.0059, 40.7128, 0.1278, 51.5074)
    ```

- You should get an answer of 5570. This is the distance from London to New York. You can check the answer online if you like, although the values will be slightly different as the Earth is not an exact sphere. It's good enough for our purposes, though.

Try a few more longitudes and latitudes from Google Maps.

