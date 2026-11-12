AI Log: MN Corn - Should there be an increase in storage before the next harvest?]

AI Tool Used: Claude AI
Prompt 1:
Build one self-contained HTML file that answers this question for a Minnesota agriculture supply chain, for my digital supply chain class: [Should our grain supply co-op increase its corn storage capacity for next harvest, based on how Minnesota corn production has trended in recent years?].
Use this data source: [quickstats.nass.usda.govquickstats.nass.usda.gov]. The fields I need are: [county/year/commodity/value/state].
Add a dropdown or slider to filter by [Year] and a chart that updates when I change it.
Add comments that explain, in plain English, where the data comes from and where it is stored.

How I checked:
1. The AI went outside the scope of sources to use, and went to a radio station's site to receive more information.  I had to cross reference data and information to ensure accuracy.

2. Cross reference my CSV insert and the spreadsheets AI pulled to add to the information and summary side of MN corn.

What went wrong:
1. I first downloaded the wrong dataset. My CSV was a Crop Progress report (week ending Nov 1, 2026), which only shows what percent of the crop is harvested. It doesn't show how much corn was produced, so it couldn't answer my storage question.

2. Instead of loading my CSV, the AI typed the production numbers directly into the code, copied from NASS PDF reports. Three of the years (2021, 2022, 2024) are rounded to the nearest 10 million bushels. The assignment warns that round numbers can mean made-up data, so I had to check them against NASS myself.

3. The first version didn't meet the requirement to load from a saved copy of the data, so I downloaded the county production CSV and had the AI change the page to load it.
