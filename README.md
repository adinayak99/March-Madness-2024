# March-Madness-2024
Kaggle competition
<br>
<br>
<p><b>Goal:</b> Forecasting the outcomes of both the men's and women's 2024 collegiate basketball tournaments.</p>
<p><b>Deadline:</b> March 21, 2024 4PM UTC (11AM EST)</p>
<br>
<br>
<h2>Dataset descriptions:</h2>
<br>
<ol>
  <li>MTeams.csv and WTeams.csv</li>
    <ul>
      <li>Teams are identified by 4-digit IDs, starting with 1 for men's and 3 for women's teams.</li>
      <li>Men's and women's team IDs for a school start with 1 and 3.</li>
      <li>Games are listed only for Division-I matchups, leading to variations in team counts across seasons.</li>
      <li>There are currently 362 men's and 360 women's Division-I teams.</li>
      <li>TeamID uniquely identifies each NCAA® men's or women's team.</li>
      <li>TeamName is a concise spelling of the college name, limited to 16 characters.</li>
      <li>FirstD1Season indicates the first season a school was Division-I; not present in WTeams.csv.</li>
      <li>LastD1Season shows the last season a school was Division-I; not present in WTeams.csv.</li>
    </ul>
  <li>MSeasons.csv and WSeasons.csv</li>
    <ul>
      <li>Separate files for men's (MSeasons) and women's data (WSeasons) identify different seasons in the historical data.</li>
      <li><b>Season:</b> Indicates the year of the tournament, with the current season labeled as 2024.</li>
      <li><b>DayZero:</b> Represents the date corresponding to DayNum=0 during the season, aligned to a common scale.</li>
      <li>RegionW, RegionX, Region Y, Region Z: Each of the four regions in the final tournament is assigned a letter of W, X, Y, or Z. The first alphabetically named region becomes Region W, the second becomes Region X, and so on. This standardizes region identification across files, regardless of region name changes. For example, during the 2012 men's tournament, the regions were East, Midwest, South, and West, designated as W/X/Y/Z respectively. The W/X/Y/Z designations for each season are determined upon the announcement of the brackets on Selection Sunday.</li>
    </ul>
</ol>
