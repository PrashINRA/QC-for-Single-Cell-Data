# QC-for-Single-Cell-Data
By default Quality Control setup of Seurat could be difficult for setting cutoffs to filter out low quality cells. 
Here I suggest and an alternative way to do this in R.

```{r}
#Load your Seurat object and take out the raw counts-
counts <- Seurat[['RNA']]@counts
counts[1:10,1:3]
genes_per_cell <- Matrix::colSums(counts>0) # count a gene only if it has non-zero reads mapped.
counts_per_cell <- Matrix::colSums(counts)
plot(sort(genes_per_cell), xlab='cell', log='y', main='genes per cell (ordered)')
```
#This will generate a plot for Cell vs Sorted (genes per cell)
You can set a threshold now in a way that it avoids lower and upper-end outliers (empty drops and doublets respectively).

![image](https://user-images.githubusercontent.com/26623347/194532393-337ee53b-4eec-45f4-8bdf-2b7881477a67.png)
