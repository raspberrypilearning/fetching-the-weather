## Fetching the latest weather

Now that you have a Weather Station to look at, you can learn how to fetch the last weather recording from that station.
This is again handled using the RESTful API of the Weather Station database. This time, the URL you need is made up of two parts. The first tells the database that you're requesting the latest measurements:

``` html
'https://apex.oracle.com/pls/apex/raspberrypi/weatherstation/getlatestmeasurements/'
```
You need to add the ID of the Weather Station you wish to access to the end of this. For example:

``` html
'https://apex.oracle.com/pls/apex/raspberrypi/weatherstation/getlatestmeasurements/1648902'
```

- Create a new Python file again, by clicking on `File` > `New File`.
- Once again, you'll need the `requests` and `json` modules, as well as `pprint`:

    ``` python
    from requests import get
    import json
    from pprint import pprint
    ```

- Now you can define a new `url` variable, but using the Weather Station ID you've chosen:

    ``` python
    url = 'https://apex.oracle.com/pls/apex/raspberrypi/weatherstation/getlatestmeasurements/weather_stn_id_goes_here'
    ```

- To get the latest measurements you need one line of code, but we'll add a second line to pretty-print it straight away:

    ``` python
    weather = get(url).json()['items']
    pprint(weather)
    ```

- You should see something like the following appearing in the shell:

    ``` json
    >>> [{'air_pressure': 1008.81,
      'air_quality': 74.9,
      'ambient_temp': 23.58,
      'created_by': 'ACRG_ROOF',
      'created_on': '2016-11-16T12:00:01Z',
      'ground_temp': 18.69,
      'humidity': 33.41,
      'id': 1669238,
      'rainfall': 0,
      'reading_timestamp': '2016-11-16T12:00:01Z',
      'updated_by': 'ACRG_ROOF',
      'updated_on': '2016-11-16T12:05:02.437Z',
      'weather_stn_id': 1648902,
      'wind_direction': 315,
      'wind_gust_speed': 0,
      'wind_speed': 0}]
    ```

- If you don't see any data, it might be because the Weather Station is offline. Just try another Weather Station Id.

