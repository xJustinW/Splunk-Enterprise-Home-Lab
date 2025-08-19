# Splunk-Enterprise-Home-Lab
This home lab will be a demonstration of my literacy and knowledge of the Splunk SIEM tool. My main goal is to achieve basic literacy in the SPL to create practical searches and functional dashboards that may be used in a SOC setting. This will also give me a baseline of understanding in SIEM tools. I am using mock information so the information may not align with a SOC environment but will suffice for the learning path of this project.

<h2>Making Efficient Searches with Visualizations</h2>
<p>There are a few ways that visualizations can be created with the SPL. I can create a variety of tables, charts, and maps which will aid in creating dashboards for later use. I can make tables of the most/least common IPs entering into the network. I can make a chart to show which services are most commonly used and specify various attributes like time of access. I can even make a map of sign-ons and utilize geolocation to show where the sign-ons are originating from in the world. In order to do this, there are some commands I will need in order to process the visualization aspect. Here are some of the visualization commands I will be making use of:</p>

- timechart
- chart
- stats
- iplocation
- geostats
- addtotals
- trendline

<p>The easiest way to get a visualization of data is to utilize the Reporting function in a field. Clicking on one of the reporting options in a field will automatically adjust the search to include both the visualization command and the field of information.</p>
<img src="https://i.imgur.com/dQm0hyj.png" height="80%" width="80%" alt="Quick Reporting"/>

<p>Notice how "timechart avg(bytes)" was appended to the end of my search automatically. This is referred to as quick reporting and is an easy option to visualize data that has been ingested into my index.</p>
<img src="https://i.imgur.com/jaaG07Q.png" height="80%" width="80%" alt="Appended Search"/>

<p>Now, I am going to create my own search that is suitable for a SOC setting and breakdown the search to show an understanding of what results are being queried for.</p>

```
index=security signature="Failed password"
| timechart count by user useother=f usenull=f limit=5
```
- ```index=security``` - This searches our security index.
- ```signature="Failed password"``` - This was a signature pulled from a failed login attempt. I used this to search for all events that had signatures for fialed password attempts. Putting this text after the index search will search specifically for that signature.
- ```timechart count by user``` - This will create a timechart based on count by user.
- ```useother=f usenull=f limit=5``` -This removed any events that had other or null values for the user and limited our showings for the top 5 offenders for failed password attempts.

<p>Here is what that search would look like.</p>
<img src="https://i.imgur.com/TkPTlCu.png" height="80%" width="80%" alt="Security Search"/>

<h2>Making a Dashboard!</h2>

<p>With the knowledge I've learned about creating visualizations, I will now create a dashbaord.</p>
<p>Here are some tips in adjusting a visualization to prepare it to be displayed on a dashboard.</p>

- I can adjust the type of chart/table/map I use by selecting this Chart dropdown.
<img src="https://i.imgur.com/bpgRudO.png" height="80%" width="80%" alt="Chart Options"/>

- I can adjust the format of the visual to make it easier to read as well as adjust the X/Y axis.
<img src="https://i.imgur.com/bGhDEKL.png" height="80%" width="80%" alt="Format Options"/>

- I can adjust the Trellis layout of the visual which will allow me to split up a chart if the information that is present is coming from multiple sources like hosts.
<img src="https://i.imgur.com/cgOHhce.png" height="80%" width="80%" alt="Trellis Options"/>

<p>Once I have adjusuted all my visuals, I can save them to a dashboard. I just simply click the "Save As" button and fill out the finishing fields from there. Here is what the dashboard looks like.</p>
<img src="https://i.imgur.com/Bp2yEWN.png" height="80%" width="80%" alt="Splunk Dashboard"/>

In a SOC setting, I would utilize the information at my hands along with collaboration with my team to come up with efficient searches to create a tuned dashboard that will allow me to monitor an organization's network.
