
## City Probing Analysis

### Preface
After creating the `measure_rtt()` probing function, I was using the provided country-specific Google domains (google.co.jp, google.de, etc.), and getting approximately 300 ms to Singapore, but at some point this was reduced to around 140 ms as seen in the figures. This was likely a result of caching, but it revealed that an actual routing to Singapore was not being done, as it was below the minimum RTT. Traceroute revealed no sign of crossing the pacific, only showing routing to New York, meaning it likely was routed to a US google CDN. This resulted in the figures shown with little difference in median RTT vs. distance. To actually measure intercontinental RTT, I tried using the Amazon EC2 domains, which was routing to the destinations and gave a more expected trend in median RTT vs. distance. These domains contain more overhead and therefore have higher inefficiency ratios that expected.


### Largest Inefficiency Ratio
My results gave London having the largest inefficiency ratio for the Amazon domains, where its RTT was similar to Tokyo despite being much closer. This is counterintuitive because London is the closest of all eight targets and is densely connected with transatlantic cables, where the EXA North/South plus the EXA express route right to the UK. This means the larger overhead dominated the propogation time, which is seen as the ratio decreases over distance generally speaking.


### Closest to Minimum RTT
Frankfurt was the closest with `358.5 - 59.0 = 299.5 ms`, which makes sense as even though it is a bit inland, it is a central European hub with strong fiber connections to the transatlantic cables, and is far enough away to avoid the overhead inefficiency cost that London had. DE-CIX Frankfurt is also the leading Internet Exchange, with great connection to Boston.

### Africa Routing through Europe
Europe has extremely high network demand and therefore have developed strong hubs. These have meant that routing up to Europe and using the existing strong Europe-America infrastracture is more cost effective than creating new America-Africa infrastructure. Additionally, there is also a cable to Brazil, which allows for the use of the cables running up the western Atlantic. Europe has also always had strong connections to Africa geopolitically, so this is demonstrating another example of that.
