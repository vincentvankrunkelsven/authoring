# Datasets

To use a dataset in your exercises, create a `datasets` folder on the root level of the repository. Every file in the `datasets` folder with a typical dataset extension, will be uploaded whenever you push the changes to GitHub. The build logs that you can find in the repository overview will inform about the upload of these datasets to DataCamp's Amazon S3 servers, and provide a link. You can then use this link in the pre_exercise_code chunk of your exercises to initialize the workspace for the student.

Example for loading in an RData file in an R exercise:


    `@pre_exercise_code`
    
    ```{r}
    load(url("http://assets.datacamp.com/production/course_123/my_file.RData"))
    ```

Example pre exercise code for loading in a CSV file in a Python exercise (with Pandas):



    `@pre_exercise_code`
          
    ```{python}
    import pandas as pd
    df = pd.read_csv('http://assets.datacamp.com/production/course_234/gapminder.csv', index_col = 0)
    ```

To limit the resource usage of the exercises, you can upload datasets up to 10Mb in size. The following extensions are supported for upload: `txt`, `csv`, `tsv`, `xls(x)`, `R`, `Rdata`, `Rds`, `Rda`, `Rmd`, `RProfile`, `Rhistory`, `hdf5`, `dta`, `p`, `sas7bdat`, `mat`, `sqlite(3)`, `db(3)`, `jp(e)g`, `png`, `sav`, `json` and `gif`. If there are other file extensions that you want to upload, please contact support.

If you want to make available self-defined functions in your R exercise, don't use an RData file to store these functions. Because of the way our submission checking system works (the student and solution code are executed in separate environments), storing functions that have been assigned in the global R environment, to later use them in an RData file causes issues. Instead, write the functions in a script that you store in your datasets folder and use `eval(parse("link_to_script_url"))` in your pre exercise code to make the functions available.

## Baking in Datasets

Currently, these datasets are automatically uploaded to S3, after which you can use R or Python code in pre-exercise code to download and import them into your session. If you have to redo this over and over again, or if your dataset is rather big, it might make sense to bake these datasets into your course image. That way, the datasets are already available when the course image spins up.

To bake a dataset into your course image, you can use the `requirements` files that you also use to install packages.

Have a look at the example below of an requirements.R for an R course. It will make the `iris.csv` available at `usr/local/share/datasets/iris.csv`.

```r
data_dir <- "usr/local/share/datasets"
dir.create(data_dir)
download.file(
  "http://s3.amazonaws.com/assets.datacamp.com/staging/course_2406/datasets/iris.csv",
  destfile = file.path(data_dir, "iris.csv")
)
```

For Python courses, you can use bash code in requirements.sh. The following snippet will also bake `iris.csv` in at `usr/local/share/datasets/iris.csv`:

```sh
DATADIR=usr/local/share/datasets/
mkdir -p $DATADIR
wget -O $DATADIR/iris.csv http://s3.amazonaws.com/assets.datacamp.com/staging/course_2406/datasets/iris.csv
```