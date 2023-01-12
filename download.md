---
layout: default
title: LocalView | Download
---

# Download

The LocalView dataset is (soon to be) hosted on <a href="https://dataverse.harvard.edu/dataverse/#" target="_blank" class="alert-link">Harvard Dataverse</a>.

From the repository, you can download it in a number of formats depending on your needs including:

* `.rds` (for R users)
* `.dta` (for Stata users)
* `.parquet` (for more advanced users who care about efficiency)
* `.json` or `.tsv` (for everyone else)

### Option 1: Download meetings manually

**Step 1.** Go to <a href="https://dataverse.harvard.edu/dataverse/#" target="_blank" class="alert-link">dataverse.harvard.edu/dataverse/placeholder</a>.

**Step 2.** Either download the individual subset and format of meetings ( `meetings.<subset>.<format>` ) that you would like or download the entire repository as a single `.zip` file.

### Option 2: Download meetings using R 

**Step 1.** Make an account on <a href="https://dataverse.harvard.edu">Harvard Dataverse</a>. Log in and retrieve (or re-generate) your [API Token](https://dataverse.harvard.edu/dataverseuser.xhtml?selectTab=apiTokenTab).

**Step 2.** Install the [`dataverse`](https://cran.r-project.org/web/packages/dataverse/index.html) package on R.

<code>
remotes::install_github("iqss/dataverse-client-r")
</code>

**Step 3.** Load the package in R and set the home server and your API token.

```
library(dataverse)

Sys.setenv("DATAVERSE_SERVER" = "https://dataverse.harvard.edu",
           "DATAVERSE_KEY" = "<my token>")
```

**Step 4.** Retrieve the particular slices of data you would like to work with (see [package tutorials](https://cran.r-project.org/web/packages/dataverse/vignettes/C-download.html)):

```
meetings.2016 <- get_dataframe_by_name(filename = "meetings.2016.tab",
                                       dataset = "XXX/XXX")
```

### Option 3: Download meetings using Python

**Step 1.** Make an account on <a href="https://dataverse.harvard.edu">Harvard Dataverse</a>. Log in and retrieve (or re-generate) your [API Token](https://dataverse.harvard.edu/dataverseuser.xhtml?selectTab=apiTokenTab).

**Step 2.** Install the [`pyDataverse`](https://pydataverse.readthedocs.io/en/latest/index.html) package on Python.

```
pip3 install pyDataverse
```

**Step 3.** Load the package in Python and set the home server and your API token.

```
from pyDataverse.api import NativeApi

api = NativeApi("https://dataverse.harvard.edu", "<my token>")
```

**Step 4.** Download the particular slices of data you would like to work with (see [package tutorials](https://pydataverse.readthedocs.io/en/latest/user/basic-usage.html)):

```
data_api = DataAccessApi('https://dataverse.harvard.edu/')

localview = api.get_dataset("doi:XXX")

data_api.get_datafile(file_id)

localview_files = localview.json()['data']['latestVersion']['files']

meetings_2016 = data_api.get_datafile("XXXX")

with open("meetings.2016.csv.zip", "wb") as f:
	f.write(response.content)
```
