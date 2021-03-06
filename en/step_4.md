## Finding a Weather Station

You can get a list of all the Weather Stations that are currently online, using a simple URL. This is because the database that all the Weather Stations upload data to has a RESTful API. This is a method by which you can write code that uses simple HTTP requests (just like a browser) to fetch the data.

Copy and paste the following URL into a web browser:

``` html
https://apex.oracle.com/pls/apex/raspberrypi/weatherstation/getallstations
```

![data from weather stations in webpage](images/website_data.PNG)

You should see a web page filled with data. This is a little difficult to read, though. Luckily, we can grab this data with a little Python code and then present it in a format that's easier to read.

- Open `IDLE Python 3`  to open the Python shell

- Open a new file by clicking `File` > `New File`.

- Save your program as `fetch_stations.py`.

- The first thing you'll need is a few Python modules. `requests`  is not in the standard library, but you can install it using the instructions from the [What you will need section](What you will need).

    ``` python
    from requests import get
    import json
    from pprint import pprint
    ```

The `requests` module allows you to fetch web pages from the World Wide Web. The `json` module allows you to easily read JSON data (which is a way of organising data into dictionaries). The `pprint` module is short for pretty-print, and just makes presenting text a little clearer.

- The next thing to do is to save that URL you used earlier as a variable:

    ``` python
    url = 'https://apex.oracle.com/pls/apex/raspberrypi/weatherstation/getallstations'
    ```

- Using `get` from the `requests` module you can now fetch the data, and translate it into Python dictionaries using the `json` module:

    ``` python
    stations = get(url).json()['items']
    ```

- Save and run your code. 

- Type `stations` into the Python shell to have a look at the data.

![look at the data in idle](images/idle_look_at_the_data.PNG)

- It still looks pretty ugly. Try typing `pprint(stations)` and see what happens. You should see a huge list of Weather Stations dictionaries. Each dictionary should look something like this:

    ``` json
     {'weather_stn_id': 1648902,
      'weather_stn_lat': 52.197834,
      'weather_stn_long': 0.125366,
      'weather_stn_name': 'ACRG_ROOF'}]
    ```

What you're seeing is:
 - `weather_stn_id` - the unique ID of the station (`weather_stn_id`) 
 - its location in the world (you will learn about this later in the project)
   - `weather_stn_lat` - the latitude
   - `weather_stn_long` - the longitude 
 - `weather_stn_name` - the name of the Weather Station.

For the next part, you're going to need to pick a Weather Station to fetch the weather from. 

- Scroll up and down the list and pick a `weather_stn_id` that you'd like to have a look at.

