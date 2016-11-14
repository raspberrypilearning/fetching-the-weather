# Fetching the Weather

One thousand weather stations were sent out to schools all over the world, at the beginning of 2016, ready to be assembled and begin collecting weather data.

Each weather station comes equipped with the sensors, shown in the table below

|Sensor Name|Purpose|
|-----------|-------|
|Rain Gauge|Measures the volume of rain falling in milimetres per square|
|Annenomter|Measures the wind speed in kilometres per hour|
|Wind Vane|Measures the wind direction in degrees|
|Soil Temperature probe|Measures the soild temperature in degrees celcius|
|Temperature sensor|Measures the air temperature in degrees celcius|
|Humidity Sensor|Measures the humidity of the air as a percentage|
|Pressure Sensor|Measures the atmospheric pressure in Pascals
|Air Quality Sensor|Measures the air quality in arbitary units|

The weather stations continually monitor the weather and then send their data to an Oracle database, where is stored and can be accessed.

In this resource you're going to learn how to find a weather station in an area close to you, and then get the latest weather updates from that station.

## Longitude and Latitude

You're going to need to find the nearest weather station to your location for this activity. You can do this because the database stores the longitude and latitude of all the weather stations around the world. Let's have a look at what we mean by longitude and latitude.

1. If you wanted to pin point a place on a 2D object like a piece of paper, you could use x and y coordinates. The x coordinate would place the points horizontal position, and the y coordinate would place the verticle position. You can see an example of this below.

    ![x and y](images/cartesian_coord.png)

1. Things aren't so simple when you're trying to pinpoint a location on a sphere, like the Earth. The vertical and horizontal positions wrap around the sphere, for a start. Also, travelling 5 units of distance along the equator would be a completely different distance to walking 5 units of distance near one of the poles. For this reason we use longitude and latitude when locating items on the Earth's surface.

1. You can draw two imaginary circles around the Earth. The first is called the Equator, which you are probably familiar with. The second is called the Prime Meridian, which passes through both the North and South poles and also through Grenwich in London.

    ![meridians](images/meridians.png)

1. The centre of these two circles is at the centre of the Earth. Imagine you were standing in the centre of the Earth, you would be able to pinpoint any location on the surface by talking about how many degrees you needed to turn within each of these circles. Longitude tells you how many degrees you need to turn East or West from the Prime meridian. Latitude tells you how many degrees you need to turn North or South from the equator.

    ![longitude and latitude](images/long_lat.gif)
    
1. The easiest way to find your longitude and latitude is to use [Google Maps](https://www.google.co.uk/maps/). You can click on any spot on the map, and your longitude and latitude will be revealed at the bottom of the screen.

    ![google maps lon and lat](images/gmaps.png)
    
1. The first number is your latitude and the second in your longitude. Make a note of the values you get, as you'll need them later.

