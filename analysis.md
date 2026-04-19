
## City Probing Analysis

### Preface
After creating the `measure_rtt()` probing function, I was using the provided country-specific Google domains (google.co.jp, google.de, etc.), and getting approximately 300 ms to Singapore, but at some point this was reduced to around 140 ms as seen in the figures. This was likely a result of caching, but it revealed that an actual routing to Singapore was not being done, as it was below the minimum RTT. Traceroute revealed no sign of crossing the pacific, only showing routing to New York, meaning it likely was routed to a US google CDN. This resulted in the figures shown with little difference in median RTT vs. distance. A second given set of university URLs as targets was done for this analysis here, but those involved much more content than a google page and had much higher RTTs.


### Largest Inefficiency Ratio
My results gave Tohoku University in Sendai having the largest inefficiency ratio of `14.81`. Looking at submarinecablemap.com, Sendai itself isn't a direct cable landing point, being about 300 km north of Tokyo on Japan's Pacific coast. Japan's major international cable landings are clustered all in the Tokyo region or further south. There are submarine cables from Sendai, but they route to Tokyo before going international. Still, it's similar in geographic distance to Seoul National University, but likely is more inefficient from their webpage having more content or redirects.


### Closest to Minimum RTT
Universidad de Chile in Santiago had the smallest gap at `716ms` (800ms measured − 84ms theoretical), which is quite interesting. Chile is geographically remote from major internet hubs, so you would expect worse routing than some of the other locations, but looking at submarinecablemap.com, Santiago to LA is served by the Curie cable owned by Google. This cable also goes through Panama, which has many cables connecting to the eastern US coast up to New York. This is likely the reason for the efficient routing.

### Africa Routing through Europe
Europe has extremely high network demand and therefore have developed strong hubs. These have meant that routing up to Europe and using the existing strong Europe-America infrastracture is more cost effective than creating new America-Africa infrastructure. Additionally, there are a few cables to Brazil, which allow for the use of the cables running up the western Atlantic, but there are not that many and this is likely due to not a strong demand for network connections between Africa and the Americas. Europe has also historically had strong connections to and influence in Africa geopolitically, so this is demonstrating another example of Europes strong ties to Africa.
