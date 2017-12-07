
# Human-readable queries

## (1) Query for all taxa
http://api.biodiversitydata.nl/v2/taxon/query

## (2) Query for all taxa and retreive 100 results (instead of 10)
http://api.biodiversitydata.nl/v2/taxon/query/?_size=100

## (3) Get the next 'batch' of 100 results
http://api.biodiversitydata.nl/v2/taxon/query/?_size=100&_from=100

## (4) Query which fields a multimedia document has
http://api.biodiversitydata.nl/v2/multimedia/metadata/getPaths
http://api.biodiversitydata.nl/v2/multimedia/metadata/getFieldInfo

## (5) Query which formats exist in multimedia documents
http://api.biodiversitydata.nl/v2/multimedia/getDistinctValues/serviceAccessPoints.format

