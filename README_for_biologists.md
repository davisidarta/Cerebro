# Biologist-friendly introduction to Cerebro

This article is meant to give an introduction to Cerebro for people who don't have any bioinformatic skills.
Maybe you are an experimental biologists who performed a scRNA-seq experiment and the computational biologists who analysed the data for you gave you a file and told you to load it into Cerebro.
And, maybe, he/she didn't tell you what Cerebro is and what it can be used for.
If this sounds like you, then this article should bring you up to speed.

To get yourself familiar with Cerebro, you don't need a real data file yet.
The application comes with a small data set pre-loaded which will allow you to get an idea of what Cerebro will show you about your own data.
If you prefer a more authentic feeling, you can also download one of the [example data sets](https://github.com/romanhaa/Cerebro/tree/master/examples) we have prepared for illustrative purposes.

## What you need

You need two things to start exploring your data:

1) The Cerebro application. The easiest way to get Cerebro is to download the standalone executable for either Windows or macOS (whichever operating system you are using) from the [Cerebro releases](https://github.com/romanhaa/Cerebro/releases). After the download is finished, the application can be unzipped and launched.
2) A file containing your data. This is the file you get from your colleague who did the analysis.

## The interface

After launching Cerebro, you will see the Cerebro dashboard with all available panels on the left.
We will go through each panel and see what information is be available there.

A few general notes:

* Please note that we have placed "info" boxes in many title bars which might provide helpful information.
* Most plots are interactive. Hover over them with your cursor to get additional information.
* Plots can be exported either to a PDF file (dimensional reductions; dedicated button in the title bar) or to a file PNG file (a small button in the top right corner of the plot that looks like a camera).
* Tables can be sorted (by clicking on the respective column title). Some can also be searched through the respective search boxes, and exported to either CSV or Excel format. Those tables which can be exported also have a "Column visibility" button which allows to hide some columns (which is useful on small screens and/or when there are many columns). Please note that in some tables some columns are hidden by default and need to be activated to be seen.

### Load data

This is the panel that we will be shown to you when you launch Cerebro.
In the top input panel you can choose your data which is the file you received from your colleague or downloaded from the examples mentioned earlier.
The input file usually has the `.crb` or `.rds` extension.
After selecting the file in the dialog box, the file will be loaded.
Please be patient during this process and wait until the progress bar says "Upload complete.".
The numbers in the different tiles will now update and give you some numbers about your data sets, including the number of cells, number of samples, number of clusters, the organism, and the experiment name.
After loading the sample, there is not much more to do here so let's move on to the "Overview" panel.

### Overview

In the "Overview" panel, you have access to all the dimensional reductions (e.g. t-SNE or UMAP) that have been generated for this data set.
Dimensional reductions can be either 2- or 3-dimensional and aim to represent the complex expression profiles of all the cells in a more interpretable way.

The plot is interactive which means you can hover over the cells with your cursor to get extra info, zoom in and out, and pan around.
You may also export the plot to a PDF image by hitting the "export to PDF" button in the title bar.
The file will the stored on your desktop.

In the input box on the left, you can select a bunch of parameters for the plot.
For example, if there are multiple dimensional reductions, you can choose which one should be shown.
Also, you can exclude entire samples or clusters from the plot.
Sometimes, data sets can become quite large which can make the plots dreadfully slow on older machines.
In those cases, consider showing only a random subset of cells by dragging the slider down from 100% to a lower value.
Next, you can choose which meta information to color the cells by.
By default, they will be colored by the sample the cells originate from, but you can change this to any meta information that is available, e.g. cluster label, cell cycle phase, etc.
The rest of the parameters are aesthetic and allow you to adjust dot size, dot opacity (transparency), and range of the X and Y scale.

### Samples

The "Samples" panel gives you a sample-centric view of the loaded data.
That means, cells are grouped by the sample they came from.

First, you'll see a table and bar plot showing you the composition of samples by the identified cluster.

Then, you will see the distribution of the number of transcripts by sample in the form of a violin plot.
More statistical info, such as the mean, median, quartiles, and min/max values, is shown when hovering over the distributions.

The same violin + box plot format is then used to show you the distribution of the number of expressed genes per sample, and, if available, also of the percentage of mitochondrial and ribosomal genes (percentage of transcripts coming from mitochondrial/ribosomal genes).

The last two boxes, if available, show the percentage of cells in the cell cycle phases calculated with two different methods (Seurat and Cyclone).

### Clusters

The "Clusters" panel gives a cluster-centric view of the data.
Except for the first plot (the cluster tree), it shows the same info as the "Samples" panel however now the cells are grouped by the cluster they were assigned to.

The cluster tree shows you the similarity between clusters.
This can be useful if you want to merge clusters and want to know which ones are most similar to each other.

Then, the composition of each cluster by sample is provided in the form of a table and plot, followed by distributions of the number of transcripts, expressed genes, and, if available, mitochondrial and ribosomal gene expression.

As before, we also see the distribution of clusters into the cell cycle phases from either Seurat or Cyclone, if they have been calculated.

### Most expressed genes

The "Most expressed genes" panel provides tables with precisely the information promised by the title.

For each sample and cluster (select in the respective input box), you will see the 100 most expressed genes and what percentage of all transcripts they account for.
Feel free to search the table through the search box, or download it in CSV or Excel format.

### Marker genes

The "Marker genes" panel provides tables of - surprise - marker genes for each sample and cluster.

In the case of marker genes per sample, this list conceptually resembles differential expression analysis of a bulk RNA-seq experiment.
Instead, the expression profiles of clusters are expected to be more homogeneous.

Marker genes should help to identify the cell type of a sample or cluster, and find new markers to purify that cell population.

It is important to know that in this analysis, each cell group (sample or cluster) is compared to all other cells combined.
This is important because it means marker genes don't have to be exclusive to one cell group.
Instead, they can be shared by multiple groups.

There are multiple parameters and cut-offs that need to be chosen during the analysis.
Check the "Marker genes" section in the "Analysis info" panel to find some details.
You can sort the genes by the average logFC, the percentage of cells that express this gene (at least 1 transcript) in the cell population of interest or the rest of cells (which it is tested against), and the adjusted p-value.
If available, by whether or not this gene might be present on the cell surface
 on the parameters used during the analysis, it might be that only genes with a positive average log-fold change of at least 0.25 are reported - meaning only over-expressed genes are shown. Also, marker genes must be expressed in at least 70% of the cells of the respective sample. Statistical analysis is performed using a classical t-test as it has been shown to be very accurate in single cell RNA-seq. Finally, if data is available, the last column reports for each gene if it is associated with gene ontology term GO:0009986 which is an indicator that the respective gene is present on the cell surface (which could make it more interesting to purify a given population).

### Enriched pathways

### Gene expression

### Gene set expression

### Trajectory

### Gene ID conversion

### Analysis info

### About

## Addendum

Before letting you go to look at your data, I want to (briefly) address one question that you might have already asked yourself: Why Cerebro?

The relationship between experimental and computational biologists can be a delicate one.
In the case of bulk RNA-seq experiments, the relationship is often relatively simple.
The exp. biologists generates his data set, prepares the library, and sends it off to sequencing.
Then, the comp. biologist will estimate gene expression values, perform differential expression analysis between experimental groups, and send the list of genes to the exp. biologist.
This is probably how it works in many examples.
Now, especially (but not only) in the context of scRNA-seq data, it's not that simple anymore.
Comp. biologists are more and more often in a position where they need to draw conclusions, make decisions how to move on because the...