# Global Population & Poverty Trends

An exploration of how population growth, fertility, life expectancy, child mortality, and extreme poverty have shifted globally and within individual countries over the last century, using data from [Gapminder.org](http://gapminder.org).

The analysis starts with a single case study — Poland, whose 20th-century population history was shaped by two world wars and a communist-to-democratic transition — then checks whether the same underlying pattern (falling child mortality → falling fertility → slowing population growth) holds across the rest of the world, before turning to a parallel look at the trajectory of global extreme poverty.

## Purpose

This project was built to:

- Practice moving from a specific question ("why did Poland's population growth slow down?") to supporting evidence across multiple linked datasets, rather than analyzing one table in isolation
- Work with real, moderately messy demographic data spanning 200+ countries and over 200 years
- Build reusable analysis functions (e.g. a function that plots any country's poverty timeline, or compares fertility vs. child mortality for any year) rather than one-off calculations
- Practice reasoning explicitly about the difference between *association* and *causation* when interpreting trends

## Key Features

- **Country case study**: a full walkthrough of Poland's population growth, fertility, life expectancy, and child mortality from 1900 onward
- **Global comparison**: the same indicators compared across the 50 most populous countries, with an interactive fertility-vs-child-mortality chart spanning 1960–2020
- **World population growth curve**: total global population from 1800 to 2020
- **Global poverty analysis**: a world map sized by the number of people in extreme poverty by country, the 10 countries with the largest poverty populations, and country-level poverty timelines (with an interactive country picker) for Poland, India, Nigeria, China, Colombia, and the United States

## How It Works

The notebook works with country-year datasets (`geo`/`time` pairs) joined together as needed — e.g. joining population and poverty-rate tables to compute absolute numbers of people in poverty, or joining fertility, child mortality, and population to build a combined scatter plot. Most of the interesting logic lives in a handful of small reusable functions:

- `fertility_over_time(country_code, start)` — a country's fertility rate from a given year onward
- `stats_for_year(year)` — population, fertility, and child mortality for the 50 most populous countries in a given year
- `fertility_vs_child_mortality(year)` — draws the fertility-vs-child-mortality scatter plot for a given year (color = region, size = population), reused both as a static chart and inside an interactive slider
- `poverty_timeline(country)` — plots a single country's number of people in extreme poverty over time, by multiplying its poverty rate and population year by year

## Tools & Skills Used

- Python, [`datascience`](https://github.com/data-8/datascience) (UC Berkeley's table-manipulation library), NumPy
- `matplotlib` for line plots, histograms, and scatter plots
- `ipywidgets` for interactive sliders and dropdowns
- Table joins, grouping/aggregation, and function-based reuse across a large notebook
- Geographic visualization (circle map sized by magnitude)

## Files Included

```
world_population_and_poverty.ipynb   <- the full analysis notebook

data/
├── population.csv        <- population by country and year
├── life_expectancy.csv   <- life expectancy at birth by country and year
├── child_mortality.csv   <- child mortality (under 5) by country and year
├── fertility.csv         <- total fertility rate by country and year
└── countries.csv         <- country names, regions, and coordinates
```

## Data Source

All data comes from Gapminder's [Systema Globalis](https://github.com/open-numbers/ddf--gapminder--systema_globalis) project, which compiles population, health, and economic statistics into a single comparable dataset — the same source this project originally cited. The `data/` files here were re-sourced directly from Gapminder's public repositories.

One dataset used in the poverty section — historical extreme-poverty rates by country and year — isn't included in `data/`, since I couldn't track down a public replacement with a matching schema. That said, every chart, table, and map in the notebook is saved as real output from the original run, so they display correctly whether or not that file is present; it only matters if someone wants to re-run the poverty section from scratch.

Note: GitHub's notebook viewer sanitizes some embedded content, so the interactive map and sliders may not render fully inline on GitHub itself — they display correctly when opened via [nbviewer.org](https://nbviewer.org) or run locally in Jupyter.

This project was inspired by an assignment for a university data science course.

## Author

Iyyah Zareef-Mustafa

## License

This project is licensed under the MIT License. See [LICENSE.txt](LICENSE.txt) for details.
