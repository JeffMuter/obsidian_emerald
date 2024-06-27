ipinfo.io is the service we're using

50k requests / month.
Last month we saw 55k users.
Need to add cookie caching to make sure we don't rerun this every time the same user reloads the page.
Specifically want the user to see a banner ONLY if they are in Arizona.
Banner sends them to: https://www.wasserstrom.com/restaurant-supplies-equipment/showcase-arizona
Only displays on the Wasserstrom.com/ homepage.

ipinfo documentation:
https://ipinfo.io/developers
[[ipinfo]]

- [x] talk to heath about UTM tracking.
- [x] implement utm tracking
- [ ] move to stage eom



PSEUDOCODE:

onLoad: 

function to get the user's location. return data object.

conditional to check data.region == AZ
if true, call makeAZBannerVisible

function makeAZBannerVisible
this function will remove the 
.AZBanner {
	display: none; css property from the banner.
}
