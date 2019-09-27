# us_tiger_roadgraph

*Work in progress - alpha version*

Notebook to generate a RAPIDS cuGraph compatible road graph, with node table, from US Census Bureau TIGER/LINE Edge vector data

Requires cudf and pyshp

To install pyshp with anaconda, use the following command:

```
conda install -c conda-forge pyshp
```

[Link to US Census Bureau TIGER/LINE data](https://www2.census.gov/geo/tiger/)

## US TIGER/LINE Documentation

[Geographic Shapefile Concepts Overview](www2.census.gov/geo/pdfs/maps-data/data/tiger/tgrshp2017/TGRSHP2017_TechDoc_Ch3.pdf)

[MAF/TIGER Feature Class Code (MTFCC) Definitions](https://www2.census.gov/geo/pdfs/maps-data/data/tiger/tgrshp2009/TGRSHP09AF.pdf)
