## Getting the weather data

Now that you can get the closest Weather Station to you, you can get the data from that weather station just like you did previously.

- Start by calling your newly created function and saving the weather station ID:

    ``` python
    closest_stn = find_closest()
    ```

- Now this can be added to the end of the `weather` variable that stores the URL. It's an integer at the moment though, so it needs to be changed to a string:

    ``` python
    weather = weather + str(closest_stn)
    ```

- Finally, you can use `requests` to get the data and then pretty-print it:

    ``` python
    my_weather = get(weather).json()['items']
    pprint(my_weather)
    ```

- Run your code and you should see the weather data for the station nearest you, printed out in the shell.

![local weather in the shell](idle_fetching_local_weather.png)