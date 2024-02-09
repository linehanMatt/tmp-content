---
title: 'How do I create a dataset using APIs?'
description: 'Use Narrative''s open APIs to create a dataset, activate the dataset, and upload files for ingestion.'
lastUpdated: '2022-05-02T15:08:34.571Z'
tags: ['Selling Data', 'Ingesting Data']
---
### Overview

Any kind of data, in any schema, can be pushed into the Narrative Data Streaming Platform as a dataset--exactly as it is stored in your own system.

Creating a dataset defines a container that will hold your raw data.

From an ingested dataset, you can use Seller Studio's customizable filters to create, package, and sell different data products on your Data Shop and/or the Data Marketplace.

Use [Narrative APIs](https://api.narrative.dev/) to programmatically create and ingest your datasets in a few steps:

1. Create the Dataset
2. Activate the Dataset
3. Upload Files for Ingestion

This how-to guide will use an adapted [nominal tuna catch dataset from the Indian Ocean Tuna Commission](https://www.iotc.org/data/datasets), with a sample below:

Fleet\_Code,IOTC\_Fishing\_Zone,Year,Fishery\_Type,Gear,Species,Species\_Latin,Species\_Group,Species\_is\_IOTC,Catch  
ARE,Western Indian Ocean,1950,Artisanal Fishing,Gillnet,Narrow-barred Spanish mackerel,Scomberomorus commerson,SEERFISH,TRUE,603  
ARE,Western Indian Ocean,1950,Artisanal Fishing,Troll line,Longtail tuna,Thunnus tonggol,TUNAS,TRUE,83  
AUS,Eastern Indian Ocean,1950,Artisanal Fishing,Unclassified,Seerfishes nei,Scomberomorus spp.,SEERFISH,TRUE,100  
CHN,Western Indian Ocean,2015,Industrial Fishing,Longline,Other non tuna-like fishes nei,Fishes non Scombroidei,OTHERS,FALSE,52  
COM,Western Indian Ocean,1950,Artisanal Fishing,Gillnet,"Non targeted, associated and dependent species",n/a,OTHERS,FALSE,10  
EUREU,Western Indian Ocean,1950,Artisanal Fishing,Hand line and Troll line,Yellowfin tuna,Thunnus albacares,TUNAS,TRUE,79  
IDN,Eastern Indian Ocean,1950,Artisanal Fishing,Beach seine,Narrow-barred Spanish mackerel,Scomberomorus commerson,SEERFISH,TRUE,6  
TWN,Eastern Indian Ocean,2019,Industrial Fishing,Longline Fresh,Hammerhead sharks nei,Sphyrna spp.,SHARKS,FALSE,0  
TZA,Western Indian Ocean,2019,Industrial Fishing,Longline,Yellowfin tuna,Thunnus albacares,TUNAS,TRUE,1  
ZAF,Western Indian Ocean,2019,Industrial Fishing,Longline targeting swordfish,Yellowfin tuna,Thunnus albacares,TUNAS,TRUE,389

An example dataset can be found at the bottom of this guide. Complete command line examples are also available in [Narrative's API documentation](https://api.narrative.dev/).

### Create the Dataset

To create a dataset, provide information about the dataset and its schema and _**POST**_ it to the Datasets API.

Dataset information provides context to buyers about your dataset and derivative data products on your Data Shop and on the Data Marketplace.

* **name**: How your dataset will be identified to you and to customers on the platform. _This should not contain spaces!_
* **description**: This appears on your dataset detail page and can explain what data is offered and how it is collected.
* **tags** (optional): Add tags to help buyers discover your dataset and its derivative products.
* **write\_mode**: This field informs how to treat new data uploaded to your dataset. Two options are supported:
  * **append**: Use if new data should be added to your dataset.
  * **overwrite**: Use if new data should replace your entire dataset.
* **schema**: Outline the properties of the dataset and provide accepted values or SQL validations. For information on defining your dataset schema, see the next section.

#### Define the Schema: Properties and Validations

The **schema** part of your dataset has a few required fields:

* **type**: This should be "object".
* **file\_config**: Indicate whether the file type is "flat" or "json".  
    If using a flat file such as a CSV file, also indicate the:

  * **delimiter**: The character separating your data file into distinct fields
  * **escape**: The character escaping a CSV string for proper parsing. For example, if your data contains a comma that is **not** meant to delimit a new row, an escape character (for example \\) would appear before the comma in your data.
  * **quote**: The character used to parse double quotes in a CSV string. If your data contains a double quote character that is **not** meant to signify a column or line break, an additional “quote” character would appear before the comma in your data. Most commonly, double quotes within values are represented by two contiguous double quotes.
  * **header**: Indicates whether the first row of a file contains field names; should be **true** or **false**

* **properties**: The fields contained in your dataset. Identify each property with a name that does not contain spaces, e.g. use "Fleet\_Code" instead of "Fleet Code".  

    Field names cannot contain spaces. Instead, use underscores ( \_ ) or camelCasing.

    The column names need not be the same as your file header names, but the columns must appear in the same order in your dataset as they do in your file.

    Each property/field must have a **type** and can have a **description**, **approximate\_cardinality**, and **enum** or **validations:**  
  * **type**: Specify the column's primitive type. Available options:

    * boolean
    * double
    * long
    * string
    * timestamptz (choose timestamptz for datetime fields)
    * object (JSON files only)
    * array (JSON files only)

        **Boolean**\-type columns will only recognize "true" and "false" values (case-insensitive, e.g. "TRUE" and "False" are also ok). Any other value will be ingested as "null".

        Choose a **string** type for columns containing text, such as identifiers, even if the identifiers consist of numbers.

        Choose a **long** type for **integers**, e.g. whole numbers and Unix timestamps.

        Choose a **double** type for **numbers with decimals**, e.g. monetary values and coordinates.

        Choose a **timestamptz** type for timestamps like "4/7/2021 11:33:07". (Choose a long type for Unix timestamps like "1606694399999".)

* * **description**: Provide information about the field. The field description, along with the name and any enumerated values or validations, will inform how your dataset field is mapped to a standard Narrative attribute.
  * **approximate\_cardinality** (optional): Providing the estimated cardinality of field values will allow your dataset to be stored and processed more efficiently.
  * **enum** (optional): Only values that are specifically _enumerated_ in the “enum” list will be considered valid. Records with any other values will not be ingested.
  * **validations** (optional): Apply validation expressions using Spark SQL.
        If a value does not pass a field validation, the record containing this value will not be ingested.
    * There is no need to apply additional validations for enumerated values outside the "enum" field.
* **required** (optional): Identify any properties that must be present for a record to be added to your dataset.
* **unsellable** (optional): Identify any properties that cannot be shared out to other parties _under any circumstance_. Including a dataset field in "unsellable" will ensure that this field cannot be transmitted on the Data Streaming Platform.
* **sensitive** (optional): Setting a field to "sensitive" ensures that the values within the field are never shown to Narrative users utilizing the UI or API (for instance, in sample APIs). Data in "sensitive" fields _will_ be delivered, in the original format, when purchased.
* **primary**: Select the single defining property in your dataset. "primary" describes the field that buyers will filter on most often, and the "primary" designation will be used to optimize the buyer experience when interacting with your dataset. _There can only be one primary field in a dataset!_
  * For example, in the Tuna Fishing dataset, the "Catch" field would be designated as the primary property because the volume of tuna caught is the most interesting data point.
  * approximate\_cardinality of the primary property is ideally around 4,000.

Once you have all required fields (**name**, **description**, **write\_mode**, **schema**), _**POST**_  the dataset metadata to the _/datasets_ endpoint to create a dataset.

The dataset will be created in "pending" state. You can change dataset information as many times as you need to until the dataset is set to "active".

If successful, you should receive a 200 response code containing your dataset ID. Save this ID to activate your dataset and ingest data.

The body of your dataset creation request should look something like this:

{  
"name":"Nominal Catches for Tuna Fishing in the Indian Ocean",  
"description":"Indian Ocean Tuna Commission (IOTC) nominal catch data on parties fishing for tunas in the Indian Ocean by year, species and gear, by vessel flag and reporting country. Reference period 1950-2019",  
"tags":\[  
"tuna",  
"fishing",  
"tuna fishing",  
"fish",  
"fishery",  
"Indian Ocean"  
\],  
"write\_mode":"append",  
"schema":{  
"file\_config":{  
"type":"flat",  
"delimiter":",",  
"escape":"\\"",  
"header":true,  
"quote":"\\""  
},  
"type":"object",  
"properties":{  
"Fleet\_Code":{  
"approximate\_cardinality":30,  
"description":"The 3-alpha code for the fleet/country performing a catch",  
"type":"string"  
},  
"IOTC\_Fishing\_Zone":{  
"approximate\_cardinality":2,  
"description":"The Indian Ocean Tuna Commission-designated zone in which tuna were caught",  
"type":"string",  
"enum":\[  
"Western Indian Ocean",  
"Eastern Indian Ocean"  
\]  
},  
"Year":{  
"approximate\_cardinality":70,  
"description":"The year of a recorded catch",  
"type":"long",  
"validations":\[  
"Year >= 1950 and Year < year(current\_timestamp)"  
\]  
},  
"Fishery\_Type":{  
"approximate\_cardinality":2,  
"description":"The classification of fishery that was performed",  
"type":"string",  
"enum":\[  
"Artisanal Fishing",  
"Industrial Fishing"  
\]  
},  
"Gear":{  
"description":"The equipment used to complete a catch. If tuna was caught bare-handed, this field will be null.",  
"type":"string"  
},  
"Species":{  
"approximate\_cardinality":50,  
"description":"The English species name of tuna or other tuna-like fish that was caught",  
"type":"string",  
"validations":\[  
"Species not like '%salmon%'"  
\]  
},  
"Species\_Latin":{  
"approximate\_cardinality":50,  
"description":"The scientific (Latin) species name of tuna or other tuna-like fish that was caught",  
"type":"string"  
},  
"Species\_Group":{  
"approximate\_cardinality":5,  
"description":"The English species group name of the fish that was caught",  
"type":"string"  
},  
"Species\_is\_IOTC":{  
"description":"Whether the species is included in the IOTC Agreement",  
"type":"boolean"  
},  
"Catch":{  
"approximate\_cardinality":30000,  
"description":"The nominal catch/capture in metric tons",  
"type":"long"  
}  
},  
"required":\[  
"Fleet\_Code",  
"IOTC\_Fishing\_Zone",  
"Year",  
"Species",  
"Species\_Latin",  
"Species\_is\_IOTC",  
"Catch"  
\],  
"primary":"/Catch"  
}

### Activate the Dataset

Activating a dataset confirms the schema and prepares the dataset to ingest raw data.

Changes cannot be made to a dataset schema once a dataset has been activated!

After confirming that your dataset has the correct metadata, columns, and validations, activate the dataset by making a _**POST**_ request to the following API endpoint: _/datasets/{dataset\_id}/activate_

### Upload Files for Ingestion

Upload new files whenever you need to update your dataset.

You can upload files using your Narrative-provided S3 bucket, or by following the API upload process outlined below.

Contact <support@narrative.io> for assistance on S3 bucket uploads.

Keep in mind that depending on the _file\_config_ used to create a dataset, each new ingestion action will either _append_ new data to the dataset or _overwrite_ the entire dataset with new data.

#### Request Upload Endpoint

First, request the endpoint to upload your file by making a **_POST_** request to the following API endpoint: _/uploads/{file\_name}_

_{file\_name}_ should be replaced with the name of the file containing your data.

The API will return a response with the details of the endpoint to use for the file upload:

{  
"path":"file123.csv",  
"url":"<https://narrative-file-upload-prod.s3.amazonaws.com/companyId%3D0/file123.csv?X-Amz-Security-Token={security\_token}>",  
"expiry":"2021-05-02T13:40:04.543Z"  
}

The security token from the response above has been removed.  The actual response will include a long string that acts as the security token, and you should keep that string intact for the next step.

#### Upload File

Next, upload the file by making a _**PUT**_ request to the _url_ parameter (so long as the expiry date has not passed).  The request body should contain the file to be uploaded.

If your file has been uploaded, you will receive a _**200**_ response code.

#### Ingest File to Dataset

Then, to push the uploaded file to your dataset for ingestion, make a _**POST**_ request to _/datasets/{dataset\_id}/upload_ with the _path_ from the upload API response in the request body:

{  
"source\_file":"{path}"  
}

Your file will be ingested within one hour.
