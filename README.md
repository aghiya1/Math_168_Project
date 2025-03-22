# Math_168_Project
This repository contains source files for our project as well as a Python notebook containing our data processing, analysis and visualization apparatus.

To see code that generated each figure in the paper, please refer to the following:
Fig 1 - Anton's Assessment/Product Scoring 
Fig 2 - Anton's Assessment/Top 2 Trading Partners/Modularity Comparison/Visualization 
Fig 3 - Aashay's Analysis/Summed and Standardized Contributions by Country 
Fig 4 - Anton's Assessment/Top 2 Trading Partners/Network Visualization (wine network)

We recommend perusing sections on most imported/exported goods as well as the assortativity visualization in Aashay's Analysis for elementary insights into the network features of all the products in the FAO dataset. These findings were not explicitly included in our report in order to preserve its scope.


Below is a more detailed outline of our Python notebook:

Chosen Products - Lists our chosen products. Pigeons were chosen subjectively. Wine, rubber, and soybeans were chosen for capturing a high fraction of nodes/edges/total volume and represent luxury, industrial, and agricultural sectors respectively (to capture differences in trading behavior for distinct product types).

Andrew's Approach - Parses FAO data into a dictionary of networks accessible by graphs[product name]

Aashay's Analysis:

**Centrality
**
Calculation - calculates metrics for each product and generates a dataframe with each row containing country name and metric. This is (pseudo)accessible via centrality_dictionary[product name]

Plot Functions
Power Law Fitting - uses scipy's curve_fit() function to estimate power law coefficients from histogram
Histogram/Barplot Generation - histograms plot values of the metric and their normalized frequency (for comparable power law fits). Barplots display the top 20 countries for a given metric and their respective values.

Visualization - visualizations of histograms (and overlaid power law fits) as well as barplots for our chosen products. also contains standardized centrality barplot from Fig 3


**Country-by-Country Analysis
**
Data Stratification - rearranges data to group metrics across all applicable products for a given country. This is (pseudo)accessible via country_dict[country name][metric]

Aggregate Measure Visualization - barplot of top 20 countries for aggregate measure for each type of centrality investigated. Average used for betweenness/closeness centrality, sum used for in/out strength, and export/import ratio calculated as sum of all in strength over all out strength for a given country.


**Most Imported/Exported Goods
**
By Country - finds products which have maximum in/out strength for a given country. This is (pseudo)accessible via country_dict[country_name][import or export]

Most Imported/Exported for High Ratio Countries - lists top imports and top exports for countries with high overall export-import ratios. 

By Product 

Restructured Data - rearranges data to find which countries have the highest import/export for a given product

Most Popular Products - bar chart of products where countries have top imports/exports. 

Top Countries for Niche Products - identifies which countries have top imports/exports for products with very few top importers/exporters.
Top Countries for Chosen Products - finds countries that have our chosen products as most imported/most exported. Note that pigeons do not make this list.

Assortativity Visualization - plots histograms of assortativity values across all products for different country groups e.g. G7, BRICS, ASEAN, EU, African Union, OPEC



Anton's Assessment:

Data Processing - reprocesses data like Andrew's Approach, but renames countries using ISO 3-letter codes.

Product Scoring - generates normalized product score plot from Fig 1.

Top 2 Trading Partners
Plot Function - filters a network so that each node only retains its top 2 edges by weight
Network Visualization - visualizes each chosen product with only the top 2 trading partners included. Wine network is from Fig 4.

Modularity Comparison
Calculation - calculates modularity values for OECD vs non-OECD nodes for a given product. simplified_modularity() does this using the product network with only the top 2 trading partners
Visualization - bar chart of changes in modularity when only top 2 trading partners are kept as seen in Fig 2


        
    
      

      
  
