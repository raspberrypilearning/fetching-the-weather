## Getting ready

At the start of this project, you fetched all the Weather Stations that are currently registered. The data came in as a huge list of dictionaries. By iterating through this list, you can pick out the longitude and latitude of the Weather Stations, and then run it through your haversine function to find the closest one.

- Create a new Python file (`File` > `New File`) and make sure you save it in the same directory as your `haversine.py` file.

- Start by importing the `requests`, `json`, and `pprint` modules that you used in Worksheet One, but you can now also import your haversine function:

    ``` python
    from requests import get
    import json
    from pprint import pprint
    from haversine import haversine
    ```

- In Worksheet One, you used two URLs to get the Weather Stations and the latest weather. You can declare these variables straight away:

    ``` python
    stations = 'https://apex.oracle.com/pls/apex/raspberrypi/weatherstation/getallstations'
    weather = 'https://apex.oracle.com/pls/apex/raspberrypi/weatherstation/getlatestmeasurements/'
    ```

- The second URL isn't complete, as you need to add the weather station ID to the end. You're going to do that in code.

- Now add in variables for your current longitude and latitude, that you found using Google Maps:

    ``` python
    my_lat = 52.194504
    my_lon = 0.134708
    ```

- To finish off this section, you can fetch the list of all stations, just like you did in Worksheet One:

``` python
all_stations = get(stations).json()['items']
```

