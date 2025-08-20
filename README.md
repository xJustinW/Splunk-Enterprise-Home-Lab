# Splunk-Enterprise-Home-Lab
<p>This home lab demonstrates my knowledge and practical use of the Splunk SIEM tool. My main goal is to achieve basic literacy in SPL (Search Processing Language) to create meaningful searches and functional dashboards that could be applied in a SOC (Security Operations Center) setting. This project also serves as a foundation for understanding SIEM tools in general.</p>
<p>I am using mock data for this lab, so the results may not fully reflect a real SOC environment. However, the dataset is sufficient for practicing and learning the core functionality of Splunk.</p>

<h2>Making Efficient Searches with Visualizations</h2>
<p>SPL provides multiple ways to create visualizations. Using commands, I can build tables, charts, and maps to aid in dashboard creation. To accomplish this, I will make use of several key visualization commands:</p>

- ```timechart```
- ```chart```
- ```stats```
- ```iplocation```
- ```geostats```
- ```addtotals```
- ```trendline```

<p>An easy way to visualize of data is utilizing the <b>Reporting</b> function in a field. Clicking on a reporting option automatically appends the appropriate SPL command and field to the search.</p>
<img src="https://i.imgur.com/dQm0hyj.png" height="80%" width="80%" alt="Quick Reporting"/>

<p>For example, notice how ```timechart avg(bytes)``` is appended to the end of a search automatically.</p>
<img src="https://i.imgur.com/jaaG07Q.png" height="80%" width="80%" alt="Appended Search"/>

<p>Now, I created my own search that is suitable for a SOC environment and here's how I breakdown the search for clarity.</p>

```
index=security signature="Failed password"
| timechart count by user useother=f usenull=f limit=5
```
- ```index=security``` - Searches the security index
- ```signature="Failed password"``` - Filters events containing the signature for failed login attempts
- ```timechart count by user``` - Builds a timechart showing counts by user
- ```useother=f usenull=f limit=5``` - Removes "other" or null values and limits results to the top 5 offenders

<p>Here is the search visualized.</p>
<img src="https://i.imgur.com/TkPTlCu.png" height="80%" width="80%" alt="Security Search"/>

<h2>Building a Dashboard!</h2>

<p>With the visualization knowledge gained, I can now create a dashboard.</p>
<p>Some options when adjusting visualizations for dashboards include:</p>

- Chart Type
- Format Options
- Trellis Layout

- I can adjust the type of chart/table/map I use by selecting this Chart dropdown.
<img src="https://i.imgur.com/bpgRudO.png" height="80%" width="80%" alt="Chart Options"/>

- I can adjust the format of the visual to make it easier to read as well as adjust the X/Y axis.
<img src="https://i.imgur.com/bGhDEKL.png" height="80%" width="80%" alt="Format Options"/>

- I can adjust the Trellis layout of the visual which will allow me to split up a chart if the information that is present is coming from multiple sources like hosts.
<img src="https://i.imgur.com/cgOHhce.png" height="80%" width="80%" alt="Trellis Options"/>

<p>Once I have adjusted all my visuals, I can save them to a dashboard. I just simply click the "Save As" button and fill out the finishing fields from there. Here is what the dashboard looks like. Again, I am using mock information to concoct these visuals.</p>
<img src="https://i.imgur.com/Bp2yEWN.png" height="80%" width="80%" alt="Splunk Dashboard"/>

<h2>Conclusion</h2>
In a SOC setting, dashboards and visualizations are critical for monitoring an organization’s environment. This project gave me practice building searches, refining visualizations, and developing dashboards using Splunk.
In a real-world scenario, I would collaborate with my team to create optimized searches and tuned dashboards that deliver actionable insights for security monitoring.
