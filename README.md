# MBTA GTFS Prep for the Vis-Society Class 2025
This is a small repo to show how we can convert GTFS ZIP archives published by the MBTA as documented [here](https://github.com/mbta/gtfs-documentation) into stops and lines in GeoJSON format. 
For this, we use a node package called [`gtfs-to-geojson`](https://github.com/blinktaginc/gtfs-to-geojson), allowing us to create `config.json` files in which we specify, which data we seek to extract from the GTFS zip file.
In the `original data` folder, you can find all the extracted geometries for stops, stops-with-buffer, lines, and lines-and-stops.
The respective `mbta_stops`, `,mbta_stops_with_buffer`, and `mbta_lines` folders are slightly cleaned versions of the datasets, where we have removed duplicated stops (i.e. stops with the same 'stop_name', 'zone_id', and 'stop_url' were removed), and duplicated lines (i.e. lines with duplicated `route_long_name` fields).

## Run the "pipeline" yourself
You can install the necessary node package by cloning this repository
```shell
$: git clone https://github.com/RicoFio/vis-society-25-gtfs-prep/
$: cd vis-society-25-gtfs-prep
```
and running
```shell
$: npm install  # we used node v23.1.0 (npm v11.1.0)
```
For the Python setup, we have used Python 3.13.1 (you can use your favorite python environment manager, e.g. [venv](https://docs.python.org/3/library/venv.html), [conda/miniconda](https://www.anaconda.com/download/success#miniconda), or [poetry](https://python-poetry.org/), to name a few) and you can run:
```shell
$: pip install -r requirements.txt
```
Finally, to run the GTFS extraction you would run
```shell
$: cd origincal_data
$: gtfs-to-geojson -c CONFIG_FILE_OF_YOUR_CHOICE 
```
And to run the attached the jupyter notebook, you would do
```shell
$: # if necessary, cd ..
$: jupyter lab
```
In the `.ipynb` file, i.e. the notebook, you can choose to do quick visualizations of the data using the GeoPandas' GeoDataFrame `.explore()` method, which is handy and why we're using this approach instead of a `.py` file.

# Who to contact
For more questions, just email `r.fiorista AT mit DOT edu`.
