# Assignment 10: Data Visualization
This semester we've spent a lot of time processing spatial datasets for the Pacific Northwest. In the past few lectures, we've talked about visualizing data and making maps. This assignment is a chance to practice pulling online data into `R`, processing unfamiliar spatial data, and making maps that combine multiple data sources and use multiple aesthetics/scales.

## Learning objectives for this assignment are:
- Prepare geospatial data in tidy format for plotting.
- Construct a map using `ggplot2` and `tmap`.
- Combine vector and raster data in the same map.
- Utilize packages that connect to online databases to pull data into `R`

## Instructions

1. After you've joined the assignment repository, you should have this file (named Readme.md) inside of a R project named assignment-10-xx where xx is your github username (or initials).

2. Once you've verified that you've correctly cloned the assignment repository, create a new Quarto document. Name this file assignment-10-xxx.qmd and give it a title (like M Williamson Assignment 10). Make sure that you select the html output option (Quarto can do a lot of cool things, but the html format is the least-likely to cause you additional headaches). We'll be using Quarto throughout the course so it's worth checking out the other tutorials in the getting started section.

3. Copy the questions below into your document and change the color of their text.

4. Save the changes and make your first commit!

5. Answer the questions making sure save and commit at least 3 more times (having 4 commits is part of the assignment).

6. Render the document to html (you should now have at least 3 files in the repository: Readme.md, assignment-10-xx.qmd, and assignment-10-xx.html). Commit these changes and push them to the repository on GitHub. You should see the files there when you go to github.com.

## The Assignment

1. Get data to visualize from the following sources:

  a. Use the `occ_search` function from `rgbif` to pull at least 1000 observations of a species of your choice in a country of your choice: `occurance.df <- occ_search(scientificName = "Any Species Name", country = "Any Country", hasCoordinate = TRUE, limit=1000)`
  
  b. Use the `geodata` package to pull a raster of interest - some variable that you think is relevant to your species. Possible functions for different types of data can be seen [here](https://github.com/rspatial/geodata?tab=readme-ov-file). Here's an example: `soils <- geodata::soil_world(var = "nitrogen", depth=5, path=tempfile())`. Use `path=tempfile()` to download a version that will be deleted when the R server restarts, but if this give you trouble, use `path=getwd()`. If you do this, _do not_ commit this data and push it to GitHub.
  
  c. Use the `geodata` package to pull in state/province/equivalent level boundaries for your country of choice using `geodata::gadm(country = "Your Country", level=1, path=tempfile())`. The same `tempfile()` instructions for part b apply here. This data will be downloaded as a `SpatVector` and can be transformed to an `sf` object with `st_as_sf()`.
  
2. Write pseudocode for how you will prepare your data for visualization. Some possible objectives might be cropping your data to an area of interest and transforming the data to tidy format.

3. Use `ggplot2` to create a map of the raster data with the species presence points overlayed on top. Add state/province/equivalent level boundaries.

4. Change the raster color scale, legend name, title, and theme from `ggplot2` defaults. You can try any other `ggplot` customization you'd like now as well.

5. Use `tmap` to recreate this plot with zooming functionality and any other interactive elements you'd like to add. Optionally, you can substitute the raster for `tidycensus` or other polygon data at this stage.
