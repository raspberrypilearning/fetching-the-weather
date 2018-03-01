## Finding the closest station

For this to work, you're going to need to run the longitude and latitude of all the stations through the haversine function. The trick will be finding the smallest distance to your current longitude and latitude, and saving this as a variable.

- Start by defining a new function, and setting a variable within it for the smallest distance. The longest possible distance between two points on the Earth's surface is 20036km, so this would be a good place to start the variable:

    ``` python
    def find_closest():
        smallest = 20036
    ```

- Now you can use a `for` loop to iterate through all the stations. Let's start by printing the data for each:

    ``` python
        for station in all_stations:
            print(station)
    ```

- Run your program and type the following into the shell to get the list of stations:

    ``` python
    find_closest()
    ```

![idle list stations](idle_find_closest.png)

You should see a large list of dictionaries, with each dictionary looking something like this:

    ``` python
    {'weather_stn_name': 'ACRG_ROOF', 'weather_stn_lat': 52.197834, 'weather_stn_id': 1648902, 'weather_stn_long': 0.125366}
    ```

The data we're interested in is the `'weather_stn_lat'` and `'weather_stn_long'`. These are the values we want to use in the haversine function.

- Go back to your program; you can now get those values in the `find_closest` function. Remove the `print(station)` line and then add the following:

    ``` python
            station_lon = station['weather_stn_long']
            station_lat = station['weather_stn_lat']
    ```

- Now that you have all the data, it can be run through the haversine function to find the station's distance to you:

    ``` python
            distance = haversine(my_lon, my_lat, station_lon, station_lat)
            print(distance)
    ```

- Run the code again and type `find_closest()` in the shell again.

That's a *long* list of distances. 

- Next, you need to find the smallest one and then save that station's ID. If the distance is smaller than the `smallest` variable it can be saved, and then next time around the loop it can be checked again.

    ``` python
            if distance < smallest:
                smallest = distance
                closest_station = station['weather_stn_id']
        return closest_station
    ```

Your `find_closest` function should now look like this:

	```python
	def find_closest():
		smallest = 20036
		for station in all_stations:
			station_lon = station['weather_stn_long']
			station_lat = station['weather_stn_lat']
			distance = haversine(my_lon, my_lat, station_lon, station_lat)
			if distance < smallest:
				smallest = distance
				closest_station = station['weather_stn_id']
		return closest_station
	```

Be really careful with the indents otherwise the function wont work properly.