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
         "value": "1004149@GEO"
       }
     ]
    }

But, more directly:

    {
     "conditions": [
       {
         "field": "gatheringEvent.siteCoordinates",
         "operator": "IN",
         "value": "Zimbabwe"
       }
     ]
    }

**But:** 
http://api.biodiversitydata.nl/v2/specimen/query/?gatheringEvent.country=Zimbabwe
gives more results, why?

## (3) Get all specimens collected in the Netherlands but not in Noord-Holland

    {
     "conditions": [
       {
         "field": "gatheringEvent.siteCoordinates.geoShape",
         "operator": "IN",
         "value": "Netherlands"
       },
       {
         "field": "gatheringEvent.siteCoordinates.geoShape",
         "operator": "NOT_IN",
         "value": "Noord-Holland"
       }
     ]
    }

## (4) Searching for non-existing values
How many records are not geo-referenced?

    {
     "conditions": [
       {
         "field": "gatheringEvent.siteCoordinates.latitudeDecimal",
         "operator": "NOT_EQUALS",
         "value": null
       },
      {
         "field": "gatheringEvent.siteCoordinates.longitudeDecimal",
         "operator": "NOT_EQUALS",
         "value": null
       }
     ]
    }

## (5) Get all specimen collected before 1900
    
    {
     "conditions": [
       {
         "field": "gatheringEvent.dateTimeBegin",
         "operator": "LT",
         "value": "1900"
       }
       ],
        "sortFields": [{"path": "gatheringEvent.dateTimeBegin", "sortOrder": "desc"}]
    }

## (6) All specimens collected between 1800 and now

     {
      "conditions": [
        {
          "field": "gatheringEvent.dateTimeBegin",
          "operator": "BETWEEN",
          "value": [
            "1800-01-01",
            "2018-01-01"
          ]
        }
      ],
       "sortFields": [{"path": "gatheringEvent.dateTimeBegin", "sortOrder": "asc"}]
    }

## (7) Are there fossils of Mackarel sharks (Lamniformes) dated to be from the Crateceous or Paloecene?

    {  
	    "conditions" : [    
		    { "field" : "identifications.defaultClassification.order", "operator" : "EQUALS", "value" : "Lamniformes" },    
		    { "field" : "gatheringEvent.chronoStratigraphy.youngChronoName", "operator" : "IN", 
		      "value" : [      "Paleocene", "Cretaceous" ] }  
	    ],  
	    "logicalOperator" : "AND",  "from" : 0,  "size" : 100
    }

