# March-Madness-2024
Kaggle competition
<br>
<br>
<p><b>Goal:</b> Forecasting the outcomes of both the men's and women's 2024 collegiate basketball tournaments.</p>
<p><b>Deadline:</b> March 21, 2024 4PM UTC (11AM EST)</p>
<br>
<br>
<h1>Dataset descriptions:</h1>
<br>
<h2>Section 1 - The Basics</h2>
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
  <br>
  <li>MSeasons.csv and WSeasons.csv</li>
    <ul>
      <li>Separate files for men's (MSeasons) and women's data (WSeasons) identify different seasons in the historical data.</li>
      <li><b>Season:</b> Indicates the year of the tournament, with the current season labeled as 2024.</li>
      <li><b>DayZero:</b> Represents the date corresponding to DayNum=0 during the season, aligned to a common scale.</li>
      <li>RegionW, RegionX, Region Y, Region Z: Each of the four regions in the final tournament is assigned a letter of W, X, Y, or Z. The first alphabetically named region becomes Region W, the second becomes Region X, and so on. This standardizes region identification across files, regardless of region name changes. For example, during the 2012 men's tournament, the regions were East, Midwest, South, and West, designated as W/X/Y/Z respectively. The W/X/Y/Z designations for each season are determined upon the announcement of the brackets on Selection Sunday.</li>
    </ul>
  <br>
  <li>MNCAATourneySeeds.csv and WNCAATourneySeeds.csv</li>
  <ul>
    <li><b>Files:</b> Identify seeds for all teams in each NCAA® tournament across historical data.</li>
    <li><b>Rows:</b> Range between 64-68 for each year, depending on play-in games.</li>
    <li><b>Structure:</b> Settles at 68 total teams in recent years, with four play-in games leading to the final field of 64 teams entering Round 1.</li>
    <li><b>Selection Sunday:</b> Seeds and teams finalized on March 17, 2024 (DayNum=132).</li>
    <li><b>Season:</b> Indicates the year of the tournament.</li>
    <li><b>Seed:</b> A 3/4-character identifier where the first character (W, X, Y, or Z) identifies the region, and the next two digits (01-16) denote the seed within the region. For play-in teams, a fourth character (a or b) distinguishes the seeds further, based on the lower numerical Team ID. For example, seed W01 represents the #1 seed in the W region.</li>
    <li><b>TeamID:</b> Identifies the ID number of the team specified in the MTeams.csv or WTeams.csv file.</li>
  </ul>
  <br>
  <li>MRegularSeasonCompactResults.csv and WRegularSeasonCompactResults.csv</li>
  <ul>
    <li><b>Files:</b> Identify game-by-game results for historical data from the 1985 season for men and the 1998 season for women.</li>
    <li><b>Season:</b> Represents the year of the associated entry in MSeasons.csv or WSeasons.csv, corresponding to the final tournament year.</li>
    <li><b>DayNum:</b> An integer ranging from 0 to 132, indicating the day the game was played. It is an offset from the "DayZero" date in the MSeasons.csv or WSeasons.csv file.</li>
    <li><b>WTeamID:</b> Identifies the ID number of the winning team listed in the MTeams.csv or WTeams.csv file.</li>
    <li><b>WScore:</b> Number of points scored by the winning team.</li>
    <li><b>LTeamID:</b> Identifies the ID number of the losing team.</li>
    <li><b>LScore:</b> Number of points scored by the losing team. WScore is always greater than LScore for all games listed.</li>
    <li><b>WLoc:</b> Identifies the "location" of the winning team: "H" for home, "A" for away, and "N" for neutral court.</li>
    <li><b>NumOT:</b> Indicates the number of overtime periods in the game, an integer 0 or higher.</li>
  </ul>
  <br>
  <li>MNCAATourneyCompactResults.csv and WNCAATourneyCompactResults.csv</li>
  <ul>
    <li><b>Files:</b> Identify game-by-game NCAA® tournament results for all historical seasons.</li>
    <li><b>Structure:</b> Formatted like RegularSeasonCompactResults data. All men's games appear as neutral site (WLoc = N), and some women's games also appear as neutral site.</li>
    <li><b>Games Listed:</b> Each season lists between 63 and 67 games, depending on the presence of play-in games.</li>
    <li><b>Round Identification (Men's Schedule):</b></li>
    <ul>
      <li>DayNum=134/135: Play-in games to reduce the field to 64 teams.</li>
      <li>DayNum=136/137: Round 1 (64 teams to 32 teams).</li>
      <li>DayNum=138/139: Round 2 (32 teams to 16 teams).</li>
      <li>DayNum=143/144: Round 3, known as "Sweet Sixteen" (16 teams to 8 teams).</li>
      <li>DayNum=145/146: Round 4, known as "Elite Eight" or "regional finals" (8 teams to 4 teams).</li>
      <li>DayNum=152: Round 5, known as "Final Four" or "national semifinals" (4 teams to 2 teams).</li>
      <li>DayNum=154: Round 6, known as "national final" or "national championship" (2 teams to 1 champion team).</li>
    </ul>
    <li><b>Other Games:</b> Post-Selection Sunday games not part of the NCAA® Tournament include postseason tournaments like NIT, CBI, CIT, and Vegas 16. These are listed in "Secondary Tourney" data files in Data Section 6.</li>
  </ul>
</ol>
<br>
<h2>Section 2 - Team Box Scores</h2>
<ol>
  <li>MRegularSeasonDetailedResults.csv and WRegularSeasonDetailedResults.csv</li>
  <ul>
    <li><b>Dataset:</b> Team-level box scores for regular seasons of historical data.</li>
    <li><b>Start Year:</b> Men's data begins with the 2003 season, while women's data starts with the 2010 season.</li>
    <li><b>Content Coverage:</b> Includes detailed results for all games listed in MRegularSeasonCompactResults file since 2003 for men and since 2010 for women.</li>
    <li><b>Data Consistency:</b> All games in MRegularSeasonCompactResults file since 2003 and WRegularSeasonCompactResults file since 2010 should be present exactly in the respective detailed results files.</li>
  </ul>
  <br>
  <li>MNCAATourneyDetailedResults.csv and WNCAATourneyDetailedResults.csv</li>
  <ul>
    <li></li>
  </ul>
</ol>

