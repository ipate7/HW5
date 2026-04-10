---
layout: page
title: "IS 445 — Building inventory (Altair)"
permalink: /
data_url: "https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/building_inventory.csv"
analysis_url: "https://github.com/ipate7/HW5/blob/main/Workbook.ipynb"
---

<p>
  <a href="{{ page.data_url }}" style="display:inline-block;padding:8px 14px;margin-right:10px;background:#0366d6;color:#fff;border-radius:6px;text-decoration:none;font-weight:600;">The Data</a>
  <a href="{{ page.analysis_url }}" style="display:inline-block;padding:8px 14px;background:#24292f;color:#fff;border-radius:6px;text-decoration:none;font-weight:600;">The Analysis</a>
</p>

## Visualization 1 — Total square footage by congressional district

<p>Total building square footage in the Illinois state inventory, summed for each U.S. congressional district. Each row is one district; bar length is total Square Footage for all buildings in that district.</p>

<p>Encodings: x is quantitative (sum of square footage). y is nominal (district id), sorted by x so the largest totals appear first. Color is quantitative mean Year Constructed by district, on a sequential viridis scale (purple for older averages, yellow-green for newer) so footprint size can be read against typical building age. Transformations: drop rows with Congress Dist equal to zero; aggregate to one row per district with sum of Square Footage, count of buildings, and mean Year Constructed where construction year was greater than zero.</p>

<iframe src="{{ '/assets/viz_congress.html' | relative_url }}" title="Congressional district totals" width="100%" height="460" style="border:0;"></iframe>

## Visualization 2 — Construction year and usage mix with brushing

<p>Top: histogram of Year Constructed (binned). Bottom: counts of buildings by Usage Description for only the rows whose construction year falls in the brushed interval. The analysis uses the ten most common usage labels, drops Year Constructed equal to zero, and keeps only year and usage for the chart data.</p>

<p>Encodings: histogram uses binned quantitative years on x and count on y. Bar chart uses nominal usage on y, count on x, and one hue per usage (legend hidden; labels on the axis). Transformations: restrict to those ten usage values, remove zero construction years, two columns retained for export size. Interactivity: an x-interval brush on the histogram drives a filter on the bar chart so the usage mix updates when you drag a different span of construction years, which compares label mixes across eras without separate controls. The vertical layout shares the x domain between panels.</p>

<iframe src="{{ '/assets/viz_brush_usage.html' | relative_url }}" title="Brush years versus usage" width="100%" height="520" style="border:0;"></iframe>
