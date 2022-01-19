# readr -- dplyr

The following homework assignment is about creating clean dataframes from 
datasets out there “in the wild”. The focus will be on learning to use the 
**readr** and **dplyr** packages along with the `%>%` (pipe) operator to create 
“recipe style” code.

-----

In a subdirectory, please create `readr_dplyr.R` where you copy-paste the 
examples below and fill in all of the missing comments marked by 
`# TODO:`. Please imagine that your comments are aimed at someone new 
to this kind of work and you want to explain what the next line of code is doing. 
Be _“clear, concise and correct”_.

-----

The basic idea of “recipe style” code is that we are going to write code that 
looks like a recipe. If we were making a cake it might look like this:

```
Cake <-
  flour %>%
  add_sugar %>%
  add_eggs %>%
  add_other_flavors %>%
  mix %>%
  pour_into_cake_pan %>%
  bake_in_oven_at_350 %>%
  remove_and_cool %>%
  add_icing %>%
  add_sprinkles
```

One of the great things about this style of coding is that it’s easy to run 
parts of it in RStudio. Just highlight a few lines up to but not including the 
final `%>%` and press Ctrl-Ret to run it:


So you can highlight and run just:

```
Cake <-
  flour
```

or

```
Cake <-
  flour %>%
  add_sugar %>%
  add_eggs %>%
  add_other_flavors %>%
  mix
```

And then check what Cake looks like at each step with `View()` or `summary()`
or `dplyr::glimpse()`.

One tricky thing you will see below is the `!!` operator which is specific to 
working with dplyr pipelines. Basically, it tells the dplyr function: “Don’t 
look for this variable inside the dataframe that is being piped in. Look for 
it outside of the current pipeline."

Example code follows:

```
# NOTE:  Install the 'jon' branch of MazamaSpatialUtils with:
# NOTE:    devtools::install_github("MazamaScience/MazamaSpatialUtils@jon") 


# TODO:  comment
library(dplyr)
# TODO:  comment
library(MazamaSpatialUtils)

# TODO:  comment
fileUrl <- paste0("http://data-lakecountyil.opendata.arcgis.com/datasets/",
                  "3e0c1eb04e5c48b3be9040b0589d3ccf_8.csv")

# TODO:  comment
col_names <- c("FID", "stateName", "obesityRate", "SHAPE_Length", "SHAPE_Area")
# TODO:  comment
col_types = "icddd"

# TODO:  comment
outputColumns <- c("stateCode", "stateName", "obesityRate")

# TODO:  comment
example_US_stateObesity <-
  # TODO:  comment
  readr::read_csv(
    file = fileUrl,
    skip = 1,                    # TODO:  comment
    col_names = col_names,
    col_types = col_types
  ) %>%
  # TODO:  comment
  dplyr::mutate(
    stateCode = MazamaSpatialUtils::US_stateNameToCode(stateName)
  ) %>%
  # TODO:  comment
  dplyr::select(!!outputColumns)

# TODO:  comment
save(example_US_stateObesity, file = "data/example_US_stateObesity.rda")

# TODO:  Please include a summary or visualization of the resulting dataframe


# TODO:  comment
library(dplyr)
# TODO:  comment
library(MazamaSpatialUtils)

# TODO:  comment
fileUrl <- "https://raw.githubusercontent.com/nytimes/covid-19-data/master/us-counties.csv"

# TODO:  comment
col_names <- c("date", "countyName", "stateName", "countyFIPS", "cases", "deaths")
# TODO:  comment
col_types = "Dcccii"

# TODO:  comment
outputColumns <- c("stateCode", "stateName", "countyFIPS", "countyName", "cases", "deaths")

# A couple of iterations and I end up with this:

# TODO:  comment
example_US_countyCovid <-
  # TODO:  comment
  readr::read_csv(
    file = fileUrl,
    skip = 1,                    # TODO:  comment
    col_names = col_names,
    col_types = col_types
  ) %>%
  # TODO:  comment
  dplyr::mutate(
    stateCode = MazamaSpatialUtils::US_stateNameToCode(stateName),
  ) %>%
  # TODO:  comment
  dplyr::filter(.data$date == lubridate::ymd("2020-06-01")) %>%
  # TODO:  comment
  dplyr::select(!!outputColumns)

# TODO:  comment
save(example_US_countyCovid, file = "example_US_countyCovid.rda")

# TODO:  Please include a summary or visualization of the resulting dataframe

```

