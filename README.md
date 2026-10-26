# Tableau dashboards: GB jobs, global health and Spotify

Three interactive dashboards on Tableau Public, each answering a question from a different dataset, plus a comparison of Tableau's products.

## At a glance

| | |
|---|---|
| **Tools** | Tableau Desktop Public Edition, Tableau Public |
| **Datasets** | EMSI job change data for 16 city areas in Great Britain (2011 and 2014); Gapminder health data (158 countries, 1990 to 2008); Spotify audio features (176,774 unique tracks) |
| **Bootcamp week** | Week 2, Days 1 and 2 (September 2026), Level 3 Data Technician Skills Bootcamp, Leep Talent |
| **Type** | Individual work on training datasets |
| **Live links** | [GB Employment Data](https://public.tableau.com/app/profile/isobel.hannington/viz/GBEmploymentData_17900040228790/GBEmploymentData) · [Global Health Insights](https://public.tableau.com/app/profile/isobel.hannington/viz/GlobalHealthInsights_17900762145110/GlobalHealthInsights) · [What makes a song popular on Spotify?](https://public.tableau.com/app/profile/isobel.hannington/viz/Week2SpotifyData/WhatmakesasongpopularonSpotify) |

## Objective

- **GB Employment:** which industries and cities gained jobs between 2011 and 2014?
- **Global Health Insights:** for a health organisation, how do life expectancy and BMI vary by continent and country, and how has life expectancy changed?
- **Spotify:** an open brief. I asked what separates popular tracks from unpopular ones.

## Data

| Dashboard | Source and size | Fields used |
|---|---|---|
| GB Employment | EMSI job change file: 16 city areas in England, Scotland and Wales, broken down into 19 industry sections and about 83 sub-industries per city | City, industry, sub-industry, Jobs 2011, Jobs 2014, Change |
| Global Health | Gapminder: 6,004 rows (158 countries, 19 years, men and women) | Continent, Country, Year, Gender, Life Expectancy, BMI, Population |
| Spotify | Spotify track features: 176,774 unique tracks across 26 genres | genre, track_id, popularity, acousticness, instrumentalness, energy, danceability, liveness, speechiness, valence |

## Approach

**GB Employment.** Bar charts of job change and job totals by industry, a city map and a treemap of sub-industries. Clicking a city or an industry filters the other charts.

**Global Health.** The brief's four charts (life expectancy by continent in 2008, a trend for the top five countries, population by gender, and life expectancy against BMI), plus BMI by continent as my own choice.

**Spotify.** Calculated fields split tracks into Hit (popularity 60+), Mid (30 to 59) and Low (under 30), and give the share of hits by distinct track. I set the cut-offs after looking at the cumulative distribution of popularity. [CONFIRM: that this is what the "High and Low cut-offs" sheet was for] I also merged two spellings of "Children's Music" (straight and curly apostrophe) into one genre.

## Skills used

**Technical**
- Calculated fields (popularity tiers, share of hits with `COUNTD`), Top N filters, quick table calculations (percentage of total) and filter actions between sheets
- Grouping to fix a duplicate category caused by different apostrophe characters

**Transferable**
- Structuring an open brief into one clear question (Spotify)
- Writing findings for a non-technical reader (see the NHS note below)

## Results and findings

### GB Employment

![GB Employment dashboard](images/gb-employment-dashboard.png)

[ADD: replace with a new screenshot once the corrected city measure is republished]

- Professional, scientific and technical activities added the most jobs (134,655), then administrative and support services (120,169) and real estate (65,387).
- Top sub-industries: real estate activities (65,387), head offices and management consultancy (57,176) and services to buildings (51,691).
- Measured as total change divided by 2011 jobs, London grew fastest (+8.7%), followed by Brighton (+4.4%). Glasgow (-2.2%), Cardiff-Newport, Leeds-Bradford and Newcastle-Sunderland all lost jobs. [CONFIRM: corrected, see fixes list]

### Global Health Insights

![Global Health Insights dashboard](images/global-health-dashboard.png)

[ADD: replace with a new screenshot once the scatter plot uses average BMI]

- In 2008, average life expectancy ranged from 77.42 years in Europe to 58.73 in Africa (Americas 73.44, Oceania 71.44, Asia 71.39). Each country counts equally; the averages aren't weighted by population.
- Average BMI was highest in Oceania (28.76) and lowest in Africa (23.46).
- For Australia, life expectancy rose from 77.0 in 1990 to 81.6 in 2008, and the 2008 population was 50.01% women.
- For the NHS: track UK average BMI alongside life expectancy, compare it with the rest of Europe, and look at BMI against cholesterol.

### What makes a song popular on Spotify?

![Spotify dashboard](images/spotify-dashboard.png)

- 9.19% of tracks are hits (popularity 60+), and average popularity is 41.1. [CONFIRM: whether this average is per track or per row]
- Hits are far less acoustic (0.23 against 0.56 for low-popularity tracks) and rarely instrumental (0.04 against 0.20). Polished, vocal-led production is the clearest difference.
- Pop, Rap and Rock are the most popular genres, and A Capella, Movie and Opera the least. Those three all sit in the low-energy, low-valence corner. But energy alone doesn't explain popularity: Ska is one of the most energetic and upbeat genres and still ranks in the bottom six. [CONFIRM: corrected, see fixes list]
- By mood, 33.79% of tracks are Happy and Energetic, 29.88% Sad and Low and 26.74% Angry and Tense.

### Tableau products compared

| Product | What it is | Cost and limits |
|---|---|---|
| Tableau Desktop Public Edition | Free authoring app | Work is published publicly to Tableau Public; fewer data connectors |
| Tableau Desktop (Creator licence) | Full authoring app | Paid; connects to a much wider range of sources [CONFIRM: corrected, see fixes list] |
| Tableau Prep Builder | Cleans and reshapes data before analysis | Included in the paid Creator licence; scheduling flows with Prep Conductor needs a paid Server or Cloud set-up [CONFIRM: corrected, see fixes list] |
| Tableau Server | Self-hosted platform for sharing and collaboration | Hosted and maintained by the organisation itself |
| Tableau Cloud | Salesforce-hosted platform | Ongoing subscription; Tableau Pulse is included in all editions [CONFIRM: corrected, see fixes list] |
| Tableau+ | Premium Tableau Cloud edition | Adds premium AI features, such as Tableau Agent in Pulse [CONFIRM: corrected, see fixes list] |

Tableau Public's main limit is that everything published is public, so it suits open or sample data only.

## Challenges and what I learned

- **Sum or average?** My scatter plot first summed BMI across 38 rows per country, pushing the axis to 1,100. Average BMI (about 20 to 31) is right. [CONFIRM: corrected, see fixes list]
- **Don't average percentages.** My city map averaged sub-industry growth rates, so a London sub-industry that went from 6 to 535 jobs inflated the figure, and Glasgow looked as if it grew when it lost jobs. Total change over total 2011 jobs gives the true rate. [CONFIRM: corrected, see fixes list]
- **Check what a filter hides.** A shared Top 10 filter on job growth leaves large industries that lost jobs, such as manufacturing, off the job-total charts. [CONFIRM: corrected, see fixes list]

## Where this applies

A sum of a rate or an average of percentages can give a figure that looks plausible and is wrong. Spotting that is the same skill an auditor uses to test how a reported number was built. For analyst roles, the dashboards show I can turn a raw extract into something a manager can use unaided.

## Repository contents

```
tableau-employment-health-spotify-dashboards/
├── README.md
└── images/
    ├── gb-employment-dashboard.png
    ├── global-health-dashboard.png
    └── spotify-dashboard.png
```

The workbooks themselves are on Tableau Public (links above), where they can be opened and downloaded.
