# Forward trajectory data

This dataset contains bird migration forward trajectory data as well as wind data for two nights. These data are generated by a forward trajectory model, using data measured by two surveillance radars. This dataset is not related to the other datasets of this case study (i.e. bird migration captured by 5 weather radars over one week), but is of the same week and countries.

## Description

The dataset is a time series. Each record represents a time (`date_time`) at which the location (`latitude` and `longitude`) of a specific bird individual, flock or particle in the wind is calculated (indicated with `track_id`). The tracks start between sunset and two hours after sunset until sunrise, in 5 minute increments. For birds, we indicate the take-off radar (`radar_id`) and start time bucket (`start_time_id`, useful for grouping data). Particles in the wind have `radar_id=3` and `start_time_id=0`. For the data on the second night, we also include airspeed (`airspeed`) in m/s for the birds (`0` for wind).

Radar `1` is located in the north of the Netherlands ("Wier"), radar `2` is located in eastern Belgium ("Glons").

## Data

* [forward_trajectory_6_7.csv](forward_trajectory_6_7.csv): Forward trajectory data for the night of April 6-7, 2013 (does not include airspeed)
* [forward_trajectory_7_8.csv](forward_trajectory_7_8.csv): Forward trajectory data for the night of April 7-8, 2013

## Methodology

The source data used by the model (see below) were gathered and processed by a bird radar detection system called [ROBIN](http://www.robinradar.com/). The ROBIN system received a radar signal from two long-range surveillance radars in the Netherlands and Belgium. Every half hour radar measurements were sampled from ten successive high-resolution images and processed to extract location, ground speed, and track direction of individual birds or flocks.

For this dataset, we used source data from the first two hours after sunset on April 6 and April 7, 2013. During this period birds take-off from the radar locations to continue their nocturnal spring migration.

For each individual bird track we extract time, location, ground speed, and track direction and calculate the airspeed and heading using the wind at 925hPa. We then use these parameters to simulate a forward trajectory based on a model described in [Shamoun-Baranes & van Gasteren 2011](http://doi.org/10.1016/j.anbehav.2011.01.003). By keeping the birds’ airspeed and heading constant, influences of wind will effect new positions each 5 minutes.

We run the model until sunrise, when nocturnal bird migration is assumed to stop. The dataset also contains wind data over a large area. For visualizations of these data, see [this blog post](http://lifewatch.inbo.be/blog/posts/forward-trajectory-visualizations.html).

## License

[Creative Commons Zero](http://creativecommons.org/publicdomain/zero/1.0/)

## Contact

[Hans van Gasteren](https://twitter.com/hvangasteren)
