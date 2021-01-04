# eclipse_data_analysis

*Heads Up* this script uses the de440t.bsp epehmerides file from JPL.
it is a *146MB* hunk of data giving the position of celestial bodies over time.
It will download the file once and use a local copy.

# Requirements

Pip3 install the folllowing packages:
 
* skyfield

### Can we predict eclipses like ancient people do?

Ancient civilisations have been able to predict eclipses to some degree just by
analyzing detailed records of when eclipses happen. 

So, in theory, we should be able to analyze the same data and predict
future eclipses without any knowledge of celestial dynamics.

# Files

## lunar_data_generation.ipynb

This notebook takes Lat/Lon/Elevation for a place on earth (wgs84 geiod, same as GPS).
It will then look at the time period of Jan 1, 1550 to Jan 1, 2640
and generate a list of lunar eclipses that are visible from that location.

It will output two files:
* {locationstr}_lunar_complete.csv - All the eclipses visible on earth, even those under horizon and penumbral eclipses
* {locationstr}_lunar_observed.csv - All the eclipses deemed "visible" at the location, Partial/Totals only

"Visible" is in quotes because it is a very generous definition of visibility.
Anything with a > 0 degree altitude is deemed "visible", even if it's barely above the horizon.
Partial eclipses count, though penumbral (where the moon is only slightly darkened) don't.

## File headings

* Visibility - str - visible / not_visible
* Altitude - float - how high in the sky the eclipse will be
* Date - str - yyyy-mm-dd format date of the eclipse
* TDB - float - Barycentric Dynamical Time - effectively Julian calendar date for us laymen
* Eclipse type - str - Total / Partial / Penumbral

# License

MIT license

