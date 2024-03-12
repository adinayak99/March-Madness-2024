# March-Madness-2024
Kaggle competition
<br>
<p><b>Goal:</b> Forecasting the outcomes of both the men's and women's 2024 collegiate basketball tournaments.</p>
<p><b>Deadline:</b> March 21, 2024 4PM UTC (11AM EST)</p>
<br>
<br>
<h1>Dataset descriptions:</h1>
<br>
<h2>Section 1 - The Basics</h2>
<p>This section provides everything you need to build a simple prediction model and submit predictions.</p>
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
<p>This section provides game-by-game stats at a team level (free throws attempted, defensive rebounds, turnovers, etc.) for all regular season, conference tournament, and NCAA® tournament games since the 2002-03 season (men) or since the 2009-10 season (women).</p>
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
    <li><b>Dataset:</b> Team-level box scores for regular seasons of historical data.</li>
    <li><b>Start Year:</b> Men's data begins with the 2003 season, while women's data starts with the 2010 season.</li>
    <li><b>Content Coverage:</b> Includes detailed results for all games listed in MRegularSeasonCompactResults file since 2003 for men and since 2010 for women.</li>
    <li><b>Data Consistency:</b> All games in MRegularSeasonCompactResults file since 2003 and WRegularSeasonCompactResults file since 2010 should be present exactly in the respective detailed results files.</li>
  </ul>
</ol>
<br>
<h2>Section 3 - Geography</h2>
<p>This section provides city locations of all regular season, conference tournament, and NCAA® tournament games since the 2009-10 season</p>
<ol>
  <li> Cities.csv</li>
  <ul>
    <li><b>Dataset:</b> Master list of cities that have been locations for games played.</li>
    <li><b>CityID:</b> A four-digit ID number uniquely identifying a city.</li>
    <li><b>City:</b> The text name of the city.</li>
    <li><b>State:</b> The state abbreviation of the state that the city is in. In rare cases, non-U.S. locations use other abbreviations (e.g., Cancun, Mexico uses "MX").</li>
  </ul>
  <li>MGameCities.csv and WGameCities.csv</li>
  <ul>
    <li><b>Dataset:</b> Game data from the 2010 season onwards, including regular season, NCAA tournament, and other post-season tournaments (men's data only).</li>
    <li><b>Season, DayNum, WTeamID, LTeamID:</b> These four columns uniquely identify each game.</li>
    <li><b>CRType:</b> Indicates the type of game (Regular, NCAA, Secondary). Regular games are found in corresponding Regular Season Compact and Detailed Results files, NCAA games in corresponding NCAA Tourney files, and Secondary games in the MSecondaryTourneyCompactResults file.</li>
    <li><b>CityID:</b> Identifies the city where the game was played, referenced from the Cities.csv file.</li>
    <li><b>Coverage:</b> Games from the 2010 season onwards are included; games from the 2009 season and earlier are not listed in this file.</li>
  </ul>
</ol>
<br>
<h2>Section 4 - Public rankings</h2>
<p>This section provides weekly team rankings (men's teams only) for dozens of top rating systems - Pomeroy, Sagarin, RPI, ESPN, etc., since the 2002-2003 season</p>
<ol>
  <li>MMasseyOrdinals.csv</li>
  <ul>
    <li><b>Dataset:</b> Contains rankings of men's teams from the 2002-2003 season onwards, based on various ranking system methodologies.</li>
    <li><b>Season:</b> Year of the associated entry in MSeasons.csv, representing the final tournament year.</li>
    <li><b>RankingDayNum:</b> Integer ranging from 0 to 133, indicating the first day appropriate for using the rankings to predict games. Final pre-tournament rankings have a RankingDayNum of 133.</li>
    <li><b>SystemName:</b> 3-letter abbreviation for each distinct ranking system.</li>
    <li><b>TeamID:</b> ID of the team being ranked, as described in MTeams.csv.</li>
    <li><b>OrdinalRank:</b> Overall ranking of the team in the underlying system.</li>
    <li><b>Disclaimer:</b> Care must be taken in methodology when using or evaluating these ranking systems due to differences in release timing and the potential impact on predictions. Rankings are typically released weekly, but their timeline may vary. For pre-tournament predictions, a conservative RankingDayNum of Wednesday is often used.</li>
 </ul>
</ol>
<br>
<h2>Section 5 - Supplements</h2>
<p>This section contains additional supporting information, including coaches, conference affiliations, alternative team name spellings, bracket structure, and game results for NIT and other postseason tournaments.</p>
<ol>
  <li>MTeamCoaches.csv</li>
  <ul>
    <li><b>Dataset:</b> Provides information about the head coach for each team in each season, including start and finish ranges of DayNums indicating mid-season coaching changes.</li>
    <li><b>Season:</b> Year of the associated entry in MSeasons.csv, representing the final tournament year.</li>
    <li><b>TeamID:</b> TeamID of the coached team, as described in MTeams.csv.</li>
    <li><b>FirstDayNum, LastDayNum:</b> Define a continuous range of days within the season when the indicated coach was the head coach of the team. FirstDayNum=0 indicates starting the year as head coach, and LastDayNum=154 indicates ending the year as head coach. Multiple records may exist for a coach in a season if there were coaching changes or leaves.</li>
    <li><b>CoachName:</b> Text representation of the coach's full name, in the format first_last, with underscores substituted for spaces.</li>
  </ul>
  <li>Conferences.csv</li>
  <ul>
    <li><b>Dataset Description:</b> Lists Division I conferences since 1985.</li>
    <li><b>ConfAbbrev:</b> Short abbreviation for each conference, used in other files to indicate the parent conference of a team or conference tournament.</li>
    <li><b>Description:</b> Longer text name for the conference.<br>
    Note: Conferences are not linked if they merged or changed names over time.<br>
    Example: "Pacific-10" conference exists up to the 2011 season, followed by a "Pacific-12" conference starting in the 2012 season, although mostly the same teams.</li>
  </ul>
  <li>MTeamConferences.csv and WTeamConferences.csv</li>
  <li>MConferenceTourneyGames.csv</li>
  <li>MSecondaryTourneyTeams.csv</li>
  <li>MSecondaryTourneyCompactResults.csv</li>
  <li>MTeamSpellings.csv and WTeamSpellings.csv</li>
  <li>MNCAATourneySlots and WNCAATourneySlots</li>
  <li>MNCAATourneySeedRoundSlots.csv</li>
</ol>
<br>
