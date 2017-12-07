## (1) Partial matching: Looking for a capybara
http://api.biodiversitydata.nl/v2/specimen/query/?identifications.defaultClassification.genus=Hydrocherus

does not give results...

    {
     "conditions": [
       {
         "field": "identifications.defaultClassification.genus",
         "operator": "STARTS_WITH",
         "value": "Hydroche"
       }
     ]
    }

for operators: see http://api.biodiversitydata.nl/v2/specimen/metadata/getFieldInfo/

## (2) Geo search: search for specimens from specific country, e.g. Zimbabwe
Specimen needs `gatheringEvent.siteCoordinates.geoShape` for that, e.g. 

http://api.biodiversitydata.nl/v2/specimen/query/?unitID=L.1213823&_fields=gatheringEvent

Zimbabwe is in geo areas: 
http://api.biodiversitydata.nl/v2/geo/query/?locality=Zimbabwe


    {
     "conditions": [
       {
         "field": "gatheringEvent.siteCoordinates.geoShape",
         "operator": "IN",
         "value": "10610481@COL"
       }
     ]
    }

    {
     "conditions": [
       {
         "field": "gatheringEvent.siteCoordinates",
         "operator": "IN",
         "value": "Zimbabwe"
       }
     ]
    }


