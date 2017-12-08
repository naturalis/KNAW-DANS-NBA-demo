
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

## (6) Get a video
http://api.biodiversitydata.nl/v2/multimedia/query/?serviceAccessPoints.format=video/mp4

## (7) Get list of collections
http://api.biodiversitydata.nl/v2/specimen/dwca/getDataSetNames

## (8) Download DWCA file for mammals collection
http://api.biodiversitydata.nl/v2/specimen/dwca/getDataSet/mammalia

## (9) Get certain field of data
http://api.biodiversitydata.nl/v2/specimen/query/?identifications.defaultClassification.genus=Hydrochoerus&_fields=unitGUID

## (10) Get two fields
http://api.biodiversitydata.nl/v2/specimen/query/?identifications.defaultClassification.genus=Hydrochoerus&_fields=unitGUID,preparationType

## (11) Sort by a field
http://api.biodiversitydata.nl/v2/geo/query/?areaType=Country&_fields=locality&_sortFields=locality:ASC

## (12) The *count* endpoint
http://api.biodiversitydata.nl/v2/specimen/count
http://api.biodiversitydata.nl/v2/specimen/count/?collectionType=Botany

