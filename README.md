# SODA (SennesOmics Data Analysis)

The aim of this experiment is to comprehensively characterize the molecular changes associated with aging around the age of 37 through multiomics analysis. The utilized omics data include Epigenomics and RNA-sequencing.
Why choose 37 instead of 42, you might ask? Well, extensive literature suggests that there are specific age-related changes occurring around 37-40 years old [1, 2, 3]. But perhaps 42 is the correct answer😊 who knows?

![image](https://github.com/CaptnClementine/SODA/assets/131146976/a3328486-5bbd-4c11-a3f5-9fc349780db8)

## Epigenomics
DNA methylation is an epigenetic mechanism that involves the addition of a methyl group to DNA molecules, typically at cytosine bases within CpG dinucleotides. This modification plays a crucial role in gene regulation, development, and various cellular processes. In the context of aging, epigenomics explores how these modifications change over time and contribute to age-related processes and diseases. 

![image](https://github.com/CaptnClementine/SODA/assets/131146976/722029fc-651c-45d3-bd65-bc80e5c63d03)

Microarray methylation data refers to information obtained through the use of microarray technology to profile DNA methylation patterns across the genome. This method allows researchers to analyze DNA methylation levels at multiple genomic loci simultaneously, providing a comprehensive view of epigenetic modifications. Microarray-based DNA methylation profiling involves enriching unmethylated and methylated DNA fractions, which are then interrogated on microarrays containing probes specific to these regions.

**Objective:**
This project aims to investigate the role of epigenomic modifications in the aging process, focusing on identifying key CpG sites and trends associated with aging.

**Workflow:**
1. **Data Collection:** Gather epigenomic data from aging cohorts, including DNA methylation profiles.
   
2. **Batch Correction:** Detect and correct for batch effects in the data to ensure accurate analysis.
   
3. **CpG Selection:** Identify relevant CpG sites for further analysis.
   
4. **CpG Group Detection:** Utilize various statistical methods and clustering techniques to detect CpG groups associated with aging.
   
5. **Trend Line Detection:** Analyze trends for each CpG group to understand their behavior with age.
   
6. **Validation:** Validate detected CpG groups using independent datasets, such as PBMC cohorts.
   
7. **GSEA Validation:** Perform Gene Set Enrichment Analysis (GSEA) within validated CpG groups to assess biological significance.
   
8. **Regression Modeling:** Construct regression models to depict age-related trends before and after specific age thresholds (e.g., 25 and 37 years old).
   
9. **Enrichment Analysis:** Conduct enrichment analysis to elucidate functional pathways associated with identified trends.
   
10. **Integration:** Merge findings from epigenomic analysis into comprehensive multi-omics analysis for a deeper understanding of aging processes.

This README.md provides an overview of the project's methodology and goals, guiding the workflow from data collection to interpretation of results.

### Data Collection, Batch Effect Correction, and CpG Selection

More than 6000 samples were found for further analysis. For the initial step, approximately 2000 samples of PBMC were collected.

<img src="https://github.com/CaptnClementine/SODA/assets/131146976/6ca1f703-4ec1-43ba-84e9-08b2fd31c6b9" style="width:50%;">

After detecting batch effects using PCA, the COMBAT method is commonly employed to correct for these effects. COMBAT (Empirical Bayes framework) works by adjusting the data to remove unwanted variation introduced by batch effects while preserving true biological signals. It achieves this by borrowing information across genes to estimate and adjust for batch effects, enhancing the accuracy of downstream analyses by harmonizing data from different batches.
![image](https://github.com/CaptnClementine/SODA/assets/131146976/3511627d-bb14-4e3f-b870-f6c0c091ca60)


The dataset GSE42861 was chosen for CpG selection due to its broad age range and ample sample size, enabling the exploration of age-related CpG methylation patterns with statistical robustness.
The selection of CpGs based on the dataset GSE42861 involved the following steps:

1. **Define Age Bins:**
Age bins were defined to categorize individuals into different age groups. The specified age bins used were: [18, 27, 30, 35, 40, 45, 60].
  
2. **Calculate Mean by Age Range:**
The dataset was then grouped by age range, and the mean values for each CpG site across different age groups were calculated.

3. **Calculate Difference in Mean Expression:**
The difference between the maximum and minimum mean expression values for each CpG site across different age ranges was calculated to assess variability in CpG expression across age groups.

4. **Count CpGs with Significant Differences:**
Finally, the number of CpGs exhibiting a significant difference in mean expression across age ranges, defined as greater than 0.05, was determined.

Based on the described process, a total of 16122 CpGs were identified for different age groups within the dataset GSE42861.

### Influence of Two CpG Group Detection Methods on Clusterization Trend Lines

The two primary principles of CpG grouping by the same age were the median and peak values of density distribution. The main pipeline after grouping remained consistent: calculating the correlation matrix of CpGs, then identifying clusters of CpGs that exhibit similar trends during aging, followed by visualization of clusters and cluster samples. 

## Transcriptomics

In the realm of transcriptomics data and microarray analysis, RNA sequencing (RNA-seq) is essential techniques for understanding gene expression changes, and as cosequenses methabolic changes in the cells and body.

RNA-seq is a powerful tool for measuring the abundance of RNA transcripts in a sample, providing insights into gene expression levels, alternative splicing, and transcript isoforms. This technique involves sequencing cDNA synthesized from RNA molecules extracted from cells or tissues, allowing researchers to quantify gene expression levels and identify differentially expressed genes under various conditions or disease states.

Microarray transcriptomics data refers to information obtained through the use of microarray technology to profile gene expression patterns across the genome. This method allows researchers to analyze gene expression levels at multiple genomic loci simultaneously, providing a comprehensive view of transcriptional activity. Microarray-based transcriptomic profiling involves hybridizing RNA samples onto microarrays containing probes specific to different genes or transcripts. By comparing gene expression patterns between samples or conditions, researchers can identifychanges about  gene expression  and gain insights into cellular processes, biological pathways, and disease mechanisms.

**Objective:** This project part aims to investigate the role of genomic modifications in the aging process, focusing on identifying key gene expression patterns and trends associated with aging.

**Workflow:**
1. **Data Collection:** Gather transcriptomic data from aging cohorts.

2. **Data annotation:** Annotation of the all data for the next steps and more careful data fusion
   
3. **Batch Correction:** Detect and correct for batch effects in the data to ensure accurate analysis.
   
4. **Gene Group Detection:** Utilize various statistical methods and clustering techniques to detect genes associated with aging.
   
5. **Trend Line Detection:** Analyze trends for each genes to understand their behavior with age.
   
6. **Validation:** Validate detected other RNAseq or microarray data using independent datasets, such as PBMC cohorts.
   
7. **GSEA Validation:** Perform Gene Set Enrichment Analysis (GSEA) within validated genes to assess biological significance.
   
8. **Regression Modeling:** Construct regression models to depict age-related trends before and after specific age thresholds (e.g., 25 and 37 years old).
   
9. **Enrichment Analysis:** Conduct enrichment analysis to elucidate functional pathways and common master regulators associated with identified trends.
   
10. **Integration:** Merge findings from epigenomic analysis into comprehensive multi-omics analysis for a deeper understanding of aging processes.

### Data collection and annotation
There are 9 datasets  where annotated and merged by the presenting common genes: GSE56047, GSE16717, GSE67220, GSE56033, GSE30483, GSE47353, GSE68759, GSE7551, GSE65907. 
There are 4588 samples collected in data, with differens ages and genders. Disrtibution of all dataest in common dataset you can see below 
![image](https://github.com/GlebBobkov/SODA/blob/transcriptomic/Age%20Distribution%20in%20Each%20Dataset.png)
![image](https://github.com/GlebBobkov/SODA/blob/transcriptomic/Summary%20of%20Dataset%20Characteristics.png)


# Links
1 https://sci-hub.ru/https://www.cambridge.org/core/journals/zygote/article/abs/antioxidant-ativities-and-lipid-peroxidation-status-in-human-follicular-fluid-agedependent-change/DD95456667D836090C97F9E3C91BC459
2 https://pubmed.ncbi.nlm.nih.gov/21451205/
3 https://sci-hub.ru/https://www.nature.com/articles/s41591-019-0673-2
