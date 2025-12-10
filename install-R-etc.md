# Install R, the Seurat R package and other R packages, and RStudio or other IDE

### IMPORTANT: This may take over an hour. You must do this before the workshop

Send email to sr110@duke.edu if you have problems. 

Please let me know if you find errors in these instructions.

#### 1 If not already installed, install R from https://cloud.r-project.org/

Select Download R for macOS or Windows (or Linux) depending on your computer's operating system.

#### 2 If not already installed, install RStudio from https://posit.co/download/rstudio-desktop/

Select choice "2: Install RStudio", assuming you already have R installed.

##### If you prefer you can use Positron: https://posit.co/products/ide/positron/ or VS Code instead


#### 3 In RStudio (or other interactive development environment), in an R console, enter the following R commands:

```r
install.packages(c('dplyr', 'Seurat', 'patchwork', 'sctransform'), repos='https://cran.rstudio.com/')
```
**Important** you need Seurat v5.  If you already have Seurat installed, to check, do
```r
packageVersion("Seurat")

```

#### 4 Make sure you can load and run a test for each of these packages

```r
library(Seurat)
pbmc_raw <- read.table(
  file = system.file('extdata', 'pbmc_raw.txt', package = 'Seurat'),
  as.is = TRUE
)
```
```r
library(dplyr)
filter(starwars, species == "Human")
```
```r
library(patchwork)
library(ggplot2)
p1 <- ggplot(mtcars) + geom_point(aes(mpg, disp))
p2 <- ggplot(mtcars) + geom_boxplot(aes(gear, disp, group = gear))

p1 + p2

```


```r
install.packages('remotes')
remotes::install_github('immunogenomics/presto', upgrade='never')
```
```r
install.packages('BiocManager')
BiocManager::install('glmGamPoi', update = FALSE)
```
(Update = FALSE because otherwise very slow to update numerous dependencies)
