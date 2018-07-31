<p align="center"><img src="https://s8.postimg.cc/y7wuenuzp/LOGO_COORDINATE_SHARP.jpg"></p>

<h2 align="center">v1.1.3.5</h2>

CoordinateSharp is a simple .NET library that is designed to assist with geographic coordinate formatting and location based celestial information. This library has the ability to convert various lat long formats, UTM, MGRS(NATO UTM) and Cartesian (X, Y, Z). 
The ability to calculate various pieces of celestial information (sunset, moon illum..) also exist.

CAUTION: v1.1.3.1 and above is considered a breaking change as `MoonDistance` has been converted from a `double?` object to a `Distance` object. Obsolete properties from 1.1.1.5 have also been removed as scheduled.

Change notes can be viewed [here](https://www.coordinatesharp.com/ChangeNotes)

### Like CoordinateSharp? Please consider donating.

[![](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=S78DZZX5KMVUS)

### Prerequisites
.NET 4.0 or .NET Standard 2.0, 1.4, 1.3 compatible runtimes.

### Installing
CoordinateSharp is available as a nuget package from [nuget.org](https://www.nuget.org/packages/CoordinateSharp/)

Alternatively, you may download the library directly [on our website](https://www.coordinatesharp.com/Download)

### Usage Example

CoordinateSharp is simple to use. In the below example we create a `Coordinate` using one of the methods below.

```csharp
//Seattle coordinates on 5 Jun 2018 @ 10:10 AM (UTC)
//Signed-Decimal Degree    47.6062, -122.3321
//Degrees Minutes Seconds  N 47º 36' 22.32" W 122º 19' 55.56"

/***********************************************************/

//Initialize with decimal degree (Standard Method)
Coordinate c = new Coordinate(47.6062, -122.3321, new DateTime(2018,6,5,10,10,0));

/***IF OTHER FORMAT IS USED SUCH AS DEGREE MINUTES SECONDS***/

//Initialize with TryParse() Method
Coordinate.TryParse("N 47º 36' 22.32\" W 122º 19' 55.56\"", new DateTime(2018,6,5,10,10,0), out c);

/****OR****/

//Initialize with Secondary Method
Coordinate c = new Coordinate();
c.Latitude = new CoordinatePart(47,36, 22.32, CoordinatePosition.N, c);
c.Longitude = new CoordinatePart(122, 19, 55.56, CoordinatePosition.W, c);
c.GeoDate = new DateTime(2018,6,5,10,10,0);
```

Once the `Coordinate` is created we have access to various formats and celestial data. Here are just a few examples.
 
 ```C#
Console.WriteLine(c);                               // N 47º 36' 22.32" W 122º 19' 55.56"
Console.WriteLine(c.Latitude.Seconds);              // 22.32
Console.WriteLine(c.UTM);                           // 10T 550200mE 5272748mN

Console.WriteLine(c.CelestialInfo.SunSet);          // 5-Jun-2018 4:02:00 AM
Console.WriteLine(c.CelestialInfo.MoonAltitude);   // 14.4169966277874
```



### Abilities
 
* Lat/Long formatting: Quickly format how a coordinate is output.
* Coordinate conversions: Convert Lat/Long to UTM, MGRS, Cartesian or vice versa.
* Coordinate parsing: Initialize a `Coordinate` with multiple format types using `TryParse()`.
* Coordinate moving/shifting: Shift coordinates using a distance and bearing, or a distance and target coordinate.
* Location based celestial information: Quickly determine sun set, moon rise, next solar eclipse or even zodiac signs at the input location.
* Property change notification: All properties automatically adjust as the `Coordinate` changes. For example, changing the `GeoDate` will cause all celestial times to recalculate. Adjusting a `Coordinate` latitudinal seconds, will retrigger all coordinate conversions and celestial data so your information is always up to date. 

### Guides

Check out the [CoordinateSharp Developer Guide](https://www.coordinatesharp.com/DeveloperGuide) for more detailed instructions on using CoordinateSharp.

You may also view the [Documentation](https://www.coordinatesharp.com/Help/index.html) for a more in depth look at CoordinateSharp's structure.
   
### Acknowledgements

Most celestial calculations are based on "Astronomical Algorithms" 2nd edition by Jean Meeus (Willmann-Bell, Richmond) 1998.

Portions of SunTime calculations were adapted from NOAA and Zacky Pickholz 2008 "C# Class for Calculating Sunrise and Sunset Times" 
 [NOAA](https://www.esrl.noaa.gov/gmd/grad/solcalc/main.js)
 [The Zacky Pickholz project](https://www.codeproject.com/Articles/29306/C-Class-for-Calculating-Sunrise-and-Sunset-Times)

Portions of MoonTime calculations were adapted from the mourner / suncalc project (c) 2011-2015, Vladimir Agafonkin [suncalc](https://github.com/mourner/suncalc/blob/master/suncalc.js)
suncalc's moon calculations are based on "Astronomical Algorithms" 2nd edition by Jean Meeus (Willmann-Bell, Richmond) 1998.
 & [These Formulas by Dr. Louis Strous](http://aa.quae.nl/en/reken/hemelpositie.html)

Portions of the calculations for illumination parameters of the moon based on [NASA Formulas](http://idlastro.gsfc.nasa.gov/ftp/pro/astro/mphase.pro) and Chapter 48 of "Astronomical Algorithms" 2nd edition by Jean Meeus (Willmann-Bell, Richmond) 1998.

UTM & MGRS Conversions were referenced from [Sami Salkosuo's j-coordconvert library](https://www.ibm.com/developerworks/library/j-coordconvert/) & [Steven Dutch, Natural and Applied Sciences,University of Wisconsin - Green Bay](https://www.uwgb.edu/dutchs/UsefulData/ConvertUTMNoOZ.HTM)

Solar and Lunar Eclipse calculations were adapted from NASA's [Eclipse Calculator](https://eclipse.gsfc.nasa.gov/) created by Chris O'Byrne and Fred Espenak.

Aspects of distance calculations referenced worked by [Ed Williams Great Circle Calculator](http://www.edwilliams.org/gccalc.htm)

Graphic and logo design work was donated by [area55](https://github.com/area55git).

<p align="center"><img src="https://s8.postimg.cc/wvf5cfpqt/LOGO_COORDINATE_SHARP_1.jpg"></p>

