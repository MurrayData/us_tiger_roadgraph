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

## New - added enumerated (MAF/TIGER Feature Class Code)

I've added enumerated mtfcc (MAF/TIGER Feature Class Code) to the road graph edges. This will allow the graph to be filterered with cudf query before applying cuGraph analysis.

Example to exclude primary roads (e.g. to build a walking graph):

```
qdf = gdf.query("mtfcc!=1")
G = cugraph.Graph()
G.add_edge_list(qdf["src"], qdf["dst"],qdf['dist'])
# Call cugraph.sssp to get the road distance from origin
start = 1000
# Filter on predecessor to elimate nodes excluded by the filter
df = cugraph.sssp(G,start).query("predecessor>=0")
```

Check output of mtfcc enumeration in notebook and refer to MTFCC documentation above for different roadtypes
