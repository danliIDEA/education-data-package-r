
<!-- README.md is generated from README.Rmd. Please edit that file -->

# educationdata

[![Travis-CI Build
Status](https://travis-ci.org/UrbanInstitute/education-data-package-r.svg?branch=master)](https://travis-ci.org/UrbanInstitute/education-data-package-r)

Retrieve data from the Urban Institute’s [Education Data
API](https://ed-data-portal.urban.org/) as a `data.frame` for easy
analysis.

## Installation

To install `educationdata`:

  - Install the `devtools` package if you don’t already have it, and
    run:

<!-- end list -->

``` r
# install.packages('devtools') # if necessary
devtools::install_github('UrbanInstitute/education-data-package-r')
```

## Usage

``` r
library(educationdata)

df <- get_education_data(level = 'schools', 
                         source = 'ccd', 
                         topic = 'enrollment', 
                         by = list('race', 'sex'),
                         filters = list(year = 2008,
                                        grade = 9:12,
                                        ncessch = '340606000122'),
                         add_labels = TRUE)

str(df)
#> 'data.frame':    96 obs. of  9 variables:
#>  $ year       : int  2008 2008 2008 2008 2008 2008 2008 2008 2008 2008 ...
#>  $ ncessch    : chr  "340606000122" "340606000122" "340606000122" "340606000122" ...
#>  $ ncessch_num: num  3.41e+11 3.41e+11 3.41e+11 3.41e+11 3.41e+11 ...
#>  $ grade      : Factor w/ 19 levels "Pre-K","Kindergarten",..: 11 11 11 11 11 11 11 11 11 11 ...
#>  $ race       : Factor w/ 14 levels "White","Black",..: 2 3 5 5 2 4 6 11 1 7 ...
#>  $ sex        : Factor w/ 7 levels "Male","Female",..: 1 1 2 1 2 2 2 1 2 1 ...
#>  $ enrollment : int  41 39 0 0 46 32 3 270 166 0 ...
#>  $ fips       : Factor w/ 80 levels "Alabama","Alaska",..: 34 34 34 34 34 34 34 34 34 34 ...
#>  $ leaid      : chr  "3406060" "3406060" "3406060" "3406060" ...
```

The `get_education_data()` function will return a `data.frame` from a
call to the Education Data API.

``` r
get_education_data(level, source, topic, by, filters, add_labels)
```

where:

  - level (required) - API data level to query.
  - source (required) - API data source to query.
  - topic (required) - API data topic to query.
  - by (optional) - Optional `list` of grouping parameters for an API
    call.
  - filters (optional) - Optional `list` query to filter the results
    from an API call.
  - add\_labels - Add variable labels (when applicable)? Defaults to
    `FALSE`.
  - csv - Download the full csv file? Defaults to `FALSE`.

## Available Endpoints

| Level              | Source    | Topic                              | By                    | Main Filters           | Years Available                               |
| :----------------- | :-------- | :--------------------------------- | :-------------------- | :--------------------- | :-------------------------------------------- |
| college-university | fsa       | campus-based-volume                | NA                    | year                   | 2001–2017                                     |
| college-university | fsa       | financial-responsibility           | NA                    | year                   | 2006–2016                                     |
| college-university | fsa       | grants                             | NA                    | year                   | 1999–2018                                     |
| college-university | fsa       | loans                              | NA                    | year                   | 1999–2018                                     |
| college-university | ipeds     | academic-libraries                 | NA                    | year                   | 2013–2016                                     |
| college-university | ipeds     | academic-year-room-board-other     | NA                    | year                   | 1999–2018                                     |
| college-university | ipeds     | academic-year-tuition-prof-program | NA                    | year                   | 1986–2008, 2010–2018                          |
| college-university | ipeds     | academic-year-tuition              | NA                    | year                   | 1986–2018                                     |
| college-university | ipeds     | admissions-enrollment              | NA                    | year                   | 2001–2017                                     |
| college-university | ipeds     | admissions-requirements            | NA                    | year                   | 1990–2017                                     |
| college-university | ipeds     | completers                         | NA                    | year                   | 2011–2016                                     |
| college-university | ipeds     | completions-cip-2                  | NA                    | year                   | 1991–2016                                     |
| college-university | ipeds     | completions-cip-6                  | NA                    | year                   | 1983–2016                                     |
| college-university | ipeds     | directory                          | NA                    | year                   | 1980, 1984–2017                               |
| college-university | ipeds     | enrollment-full-time-equivalent    | NA                    | year, level\_of\_study | 1997–2016                                     |
| college-university | ipeds     | enrollment-headcount               | NA                    | year, level\_of\_study | 1996–2016                                     |
| college-university | ipeds     | fall-enrollment                    | age, sex              | year, level\_of\_study | 1991, 1993, 1995, 1997, 1999–2017             |
| college-university | ipeds     | fall-enrollment                    | race, sex             | year, level\_of\_study | 1986–2017                                     |
| college-university | ipeds     | fall-enrollment                    | residence             | year                   | 1986, 1988, 1992, 1994, 1996, 1998, 2000–2017 |
| college-university | ipeds     | fall-retention                     | NA                    | year                   | 2003–2017                                     |
| college-university | ipeds     | finance                            | NA                    | year                   | 1979, 1983–2017                               |
| college-university | ipeds     | grad-rates-200pct                  | NA                    | year                   | 2007–2016                                     |
| college-university | ipeds     | grad-rates-pell                    | NA                    | year                   | 2015–2016                                     |
| college-university | ipeds     | grad-rates                         | NA                    | year                   | 1996–2016                                     |
| college-university | ipeds     | institutional-characteristics      | NA                    | year                   | 1980, 1984–2017                               |
| college-university | ipeds     | outcome-measures                   | NA                    | year                   | 2015–2016                                     |
| college-university | ipeds     | program-year-room-board-other      | NA                    | year                   | 1999–2018                                     |
| college-university | ipeds     | program-year-tuition-cip           | NA                    | year                   | 1987–2018                                     |
| college-university | ipeds     | sfa-all-undergraduates             | NA                    | year                   | 2007–2017                                     |
| college-university | ipeds     | sfa-by-living-arrangement          | NA                    | year                   | 2008–2017                                     |
| college-university | ipeds     | sfa-by-tuition-type                | NA                    | year                   | 1999–2017                                     |
| college-university | ipeds     | sfa-ftft                           | NA                    | year                   | 1999–2017                                     |
| college-university | ipeds     | sfa-grants-and-net-price           | NA                    | year                   | 2008–2017                                     |
| college-university | ipeds     | student-faculty-ratio              | NA                    | year                   | 2009–2017                                     |
| college-university | nhgis     | census-1990                        | NA                    | year                   | 1980, 1984–2017                               |
| college-university | nhgis     | census-2000                        | NA                    | year                   | 1980, 1984–2017                               |
| college-university | nhgis     | census-2010                        | NA                    | year                   | 1980, 1984–2017                               |
| college-university | scorecard | default                            | NA                    | year                   | 1996–2017                                     |
| college-university | scorecard | earnings                           | NA                    | year                   | 2003–2014                                     |
| college-university | scorecard | institutional-characteristics      | NA                    | year                   | 1996–2017                                     |
| college-university | scorecard | repayment                          | NA                    | year                   | 2007–2016                                     |
| college-university | scorecard | student-characteristics            | aid-applicants        | year                   | 1997–2016                                     |
| college-university | scorecard | student-characteristics            | home-neighborhood     | year                   | 1997–2016                                     |
| school-districts   | ccd       | directory                          | NA                    | year                   | 1986–2018                                     |
| school-districts   | ccd       | enrollment                         | NA                    | year, grade            | 1986–2018                                     |
| school-districts   | ccd       | enrollment                         | race                  | year, grade            | 1986–2018                                     |
| school-districts   | ccd       | enrollment                         | race, sex             | year, grade            | 1986–2018                                     |
| school-districts   | ccd       | enrollment                         | sex                   | year, grade            | 1986–2018                                     |
| school-districts   | ccd       | finance                            | NA                    | year                   | 1991, 1994–2016                               |
| school-districts   | edfacts   | assessments                        | NA                    | year, grade\_edfacts   | 2009–2017                                     |
| school-districts   | edfacts   | assessments                        | race                  | year, grade\_edfacts   | 2009–2017                                     |
| school-districts   | edfacts   | assessments                        | sex                   | year, grade\_edfacts   | 2009–2017                                     |
| school-districts   | edfacts   | assessments                        | special-populations   | year, grade\_edfacts   | 2009–2017                                     |
| school-districts   | saipe     | NA                                 | NA                    | year                   | 1995, 1997, 1999–2018                         |
| schools            | ccd       | directory                          | NA                    | year                   | 1986–2018                                     |
| schools            | ccd       | enrollment                         | NA                    | year, grade            | 1986–2018                                     |
| schools            | ccd       | enrollment                         | race                  | year, grade            | 1986–2018                                     |
| schools            | ccd       | enrollment                         | race, sex             | year, grade            | 1986–2018                                     |
| schools            | ccd       | enrollment                         | sex                   | year, grade            | 1986–2018                                     |
| schools            | crdc      | ap-exams                           | disability, sex       | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | ap-exams                           | lep, sex              | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | ap-exams                           | race, sex             | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | ap-ib-enrollment                   | disability, sex       | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | ap-ib-enrollment                   | lep, sex              | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | ap-ib-enrollment                   | race, sex             | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | chronic-absenteeism                | disability, sex       | year                   | 2013, 2015                                    |
| schools            | crdc      | chronic-absenteeism                | lep, sex              | year                   | 2013, 2015                                    |
| schools            | crdc      | chronic-absenteeism                | race, sex             | year                   | 2013, 2015                                    |
| schools            | crdc      | directory                          | NA                    | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | discipline                         | disability, lep, sex  | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | discipline                         | disability, race, sex | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | discipline                         | disability, sex       | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | enrollment                         | disability, sex       | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | enrollment                         | lep, sex              | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | enrollment                         | race, sex             | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | harassment-or-bullying             | allegations           | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | harassment-or-bullying             | disability, sex       | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | harassment-or-bullying             | lep, sex              | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | harassment-or-bullying             | race, sex             | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | restraint-and-seclusion            | disability, lep, sex  | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | restraint-and-seclusion            | disability, race, sex | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | restraint-and-seclusion            | disability, sex       | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | restraint-and-seclusion            | instances             | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | sat-act-participation              | disability, sex       | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | sat-act-participation              | lep, sex              | year                   | 2011, 2013, 2015                              |
| schools            | crdc      | sat-act-participation              | race, sex             | year                   | 2011, 2013, 2015                              |
| schools            | edfacts   | assessments                        | NA                    | year, grade\_edfacts   | 2009–2017                                     |
| schools            | edfacts   | assessments                        | race                  | year, grade\_edfacts   | 2009–2017                                     |
| schools            | edfacts   | assessments                        | sex                   | year, grade\_edfacts   | 2009–2017                                     |
| schools            | edfacts   | assessments                        | special-populations   | year, grade\_edfacts   | 2009–2017                                     |
| schools            | nhgis     | census-1990                        | NA                    | year                   | 1986–2016                                     |
| schools            | nhgis     | census-2000                        | NA                    | year                   | 1986–2016                                     |
| schools            | nhgis     | census-2010                        | NA                    | year                   | 1986–2016                                     |

## Main Filters

Due to the way the API is set-up, the variables listed within ‘main
filters’ are the fastest way to subset an API call.

In addition to `year`, the other main filters for certain endpoints
accept the following values:

### Grade

| Filter Argument      | Grade            |
| -------------------- | ---------------- |
| `grade = 'grade-pk'` | Pre-K            |
| `grade = 'grade-k'`  | Kindergarten     |
| `grade = 'grade-1'`  | Grade 1          |
| `grade = 'grade-2'`  | Grade 2          |
| `grade = 'grade-3'`  | Grade 3          |
| `grade = 'grade-4'`  | Grade 4          |
| `grade = 'grade-5'`  | Grade 5          |
| `grade = 'grade-6'`  | Grade 6          |
| `grade = 'grade-7'`  | Grade 7          |
| `grade = 'grade-8'`  | Grade 8          |
| `grade = 'grade-9'`  | Grade 9          |
| `grade = 'grade-10'` | Grade 10         |
| `grade = 'grade-11'` | Grade 11         |
| `grade = 'grade-12'` | Grade 12         |
| `grade = 'grade-13'` | Grade 13         |
| `grade = 'grade-14'` | Adult Education  |
| `grade = 'grade-15'` | Ungraded         |
| `grade = 'grade-16'` | K-12             |
| `grade = 'grade-20'` | Grades 7 and 8   |
| `grade = 'grade-21'` | Grade 9 and 10   |
| `grade = 'grade-22'` | Grades 11 and 12 |
| `grade = 'grade-99'` | Total            |

### Level of Study

| Filter Argument                         | Level of Study     |
| --------------------------------------- | ------------------ |
| `level_of_study = 'undergraduate'`      | Undergraduate      |
| `level_of_study = 'graduate'`           | Graduate           |
| `level_of_study = 'first-professional'` | First Professional |
| `level_of_study = 'post-baccalaureate'` | Post-baccalaureate |
| `level_of_study = '99'`                 | Total              |

## Examples

Let’s build up some examples, from the following set of endpoints.

| Level   | Source | Topic      | By              | Main Filters | Years Available  |
| :------ | :----- | :--------- | :-------------- | :----------- | :--------------- |
| schools | ccd    | enrollment | NA              | year, grade  | 1986–2018        |
| schools | ccd    | enrollment | race            | year, grade  | 1986–2018        |
| schools | ccd    | enrollment | race, sex       | year, grade  | 1986–2018        |
| schools | ccd    | enrollment | sex             | year, grade  | 1986–2018        |
| schools | crdc   | enrollment | disability, sex | year         | 2011, 2013, 2015 |
| schools | crdc   | enrollment | lep, sex        | year         | 2011, 2013, 2015 |
| schools | crdc   | enrollment | race, sex       | year         | 2011, 2013, 2015 |

The following will return a `data.frame` across all years and grades:

``` r
library(educationdata)
df <- get_education_data(level = 'schools', 
                         source = 'ccd', 
                         topic = 'enrollment')
```

Note that this endpoint is also callable `by` certain variables:

  - race
  - sex
  - race, sex

These variables can be added to the `by` argument:

``` r
df <- get_education_data(level = 'schools', 
                         source = 'ccd', 
                         topic = 'enrollment', 
                         by = list('race', 'sex'))
```

You may also filter the results of an API call. In this case `year` and
`grade` will provide the most time-efficient subsets, and can be
vectorized:

``` r
df <- get_education_data(level = 'schools', 
                         source = 'ccd', 
                         topic = 'enrollment', 
                         by = list('race', 'sex'),
                         filters = list(year = 2008,
                                        grade = 9:12))
```

Additional variables can also be passed to `filters` to subset further:

``` r
df <- get_education_data(level = 'schools', 
                         source = 'ccd', 
                         topic = 'enrollment', 
                         by = list('race', 'sex'),
                         filters = list(year = 2008,
                                        grade = 9:12,
                                        ncessch = '3406060001227'))
```

The `add_labels` flag will map variables to a `factor` from their labels
in the API.

``` r
df <- get_education_data(level = 'schools', 
                         source = 'ccd', 
                         topic = 'enrollment', 
                         by = list('race', 'sex'),
                         filters = list(year = 2008,
                                        grade = 9:12,
                                        ncessch = '340606000122'),
                         add_labels = TRUE)
```

Finally, the `csv` flag can be set to download the full `.csv` data
frame. In general, the `csv` functionality is much faster when
retrieving the full data frame (or a large subset) and much slower when
retrieving a small subset of a data frame (especially ones with a lot of
`filters` added). In this example, the full `csv` for 2008 must be
downloaded and then subset to the 96 observations.

``` r
df <- get_education_data(level = 'schools', 
                         source = 'ccd', 
                         topic = 'enrollment', 
                         by = list('race', 'sex'),
                         filters = list(year = 2008,
                                        grade = 9:12,
                                        ncessch = '340606000122'),
                         add_labels = TRUE,
                         csv = TRUE)
```
