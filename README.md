[![](https://jitpack.io/v/MohammedMokresh/androidGeoHash.svg)](https://jitpack.io/#MohammedMokresh/androidGeoHash)


# androidGeoHash

A geohash is a convenient way of expressing a location (anywhere in the world) using a short alphanumeric string,
with greater precision obtained with longer strings.

A geohash actually identifies a rectangular cell: at each level, each extra character identifies one of 32 sub-cells.



 Nearby locations generally have similar prefixes, though not always: there are edge-cases straddling large-cell boundaries; in France, La Roche-Chalais (u000) is just 30km from Pomerol (ezzz). A reliable prefix search for proximate locations will also search prefixes of a cell’s 8 neighbours. (e.g. a database query for results within 30-odd kilometres of Pomerol would be SELECT * FROM MyTable WHERE LEFT(Geohash, 4) IN ('ezzz', 'gbpb, 'u000', 'spbp', 'spbn', 'ezzy', 'ezzw', 'ezzx', 'gbp8'). Whether this would offer significant (or any) performance gains over a latitude/longitude bounding box search I’ve yet to check.


**Step 1.** Add the JitPack repository to your build file
Add it in your root build.gradle at the end of repositories:

	allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}


**Step 2.** Add the dependency

	dependencies {
		implementation 'com.github.MohammedMokresh:androidGeoHash:v1.0'
	}

# Example


` public string getTheGeoHash(){
  Location location = new Location("geohash");
  location.setLatitude(53.84543);
  location.setLongitude(86.88464);
 
  GeoHash hash = GeoHash.fromLocation(location, 9);
  return hash.toString(); //"vctf3472q"
}



