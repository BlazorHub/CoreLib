﻿# Geo Location

# Interfaces
* IGeoLocation - Interface to store a Geo Location with decimal and DMS Coordinates
* IGeoCoordinate - Interface to store a Geo Coordinate in (DMS) degrees, minute, second (and millisecond) format. 
* IGeoCoordinateMath - Interface to convert decimal coordinates into DMS (IGeoCoordinate) coordinates.
* IGeoCoordinateFormatter - Interface to format a DMS coordinate to string

# Factory Interfaces
* IGeoLocationFactory - Interface to create a IGeoLocation instances from longitude and latitude 

# Examples

```csharp
var factory  = new DefaultGeoLocationFactory();
var location = factory.Create(52.518639M, 13.376090M);

// access longitude and latiduce in decimal and DMS format via properties.
// Note: calculation of DMS coordinates (IGeoCoordinateMath) and formatting (IGeoCoordinateFormatter) is exchangeable
```

Format Geo Coordinates (DMS) to string
```csharp
var location = new DefaultGeoLocationFactory().Create(52.518639M, 13.376090M);

// ToString is overwritten and uses the default formatter
var latDMSStr = location.LatitudeDMS.ToString();  // N 52° 31' 07.1"
var lonDMSStr = location.LongitudeDMS.ToString(); // E 13° 22' 33.9"
```

Custom formatting of Geo Coordinates (DMS)
```csharp
var location = new DefaultGeoLocationFactory().Create(52.518639M, 13.376090M);

// TODO: implement your own DMS coordinate formatter and replace the default formatter
IGeoCoordinateFormatter formatter = new DefaultGeoCoordinateFormatter();

var latDMSViaFormatter = formatter.WriteToString(location.LatitudeDMS); // N 52° 31' 07.1"
var lonDMSViaFormatter = formatter.WriteToString(location.LatitudeDMS); // E 13° 22' 33.9"
```