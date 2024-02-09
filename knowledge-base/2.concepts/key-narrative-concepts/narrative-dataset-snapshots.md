---
title: 'Narrative Snapshot Documentation'
description: 'Learn how Narrative utilizes snapshots to express how datasets change over time. '
lastUpdated: '2022-12-16T19:28:46.247Z'
tags: ['Integrations & Technical Guides', 'Narrative Syncs & Processes']
---
### Introduction

Narrative leverages [Iceberg Tables](https://iceberg.apache.org/spec/#:~:text=A%20snapshot%20represents%20the%20state,partition%20data%2C%20and%20its%20metrics.) to store large amounts of data. One of Iceberg's core principles is utilizing snapshots to store and reference a collection of files. **A snapshot represents the state of a dataset at a point in time** and is used to access the complete set of data files behind a dataset. Snapshots are recorded through manifest files that contain a row for each data file in the table with its metrics. The complete picture of dataset is shown by joining together all the data files for a manifest. Every manifest holds metadata about the data, including partition stats and data file counts. **These stats are used to skip over manifests that are not required for an operation.** Narrative uses these efficiencies to save time when displaying information on a dataset's statistics and retention policies.

### Narrative Snapshot Use Cases

#### **Dataset Retention Policies**

Narrative wants to prevent suppliers from having to house data that they deem useless. Dataset retention policies allow users to control the size of their datasets by defining how long they want to keep data stored in Narrative's ecosystem. Properly set up dataset retention policies will allow providers to keep storage costs down and prevent buyers from scanning unnecessary aged data.

Snapshots assist retention policies by allowing sellers to query previous versions of their dataset to understand how their file size changes over time. This is useful for sellers who want to know how much data was expired and when. Storing data in snapshots also allows providers to delete data at the file level instead of the row level, which avoids painful processing costs to rewrite the entire dataset.

Users may update a dataset's retention policy one dataset at a time. For example, the following retention policy (json request) will expire data that has been in a single dataset after 30 days when sent to: <https://api.narrative.io/datasets/{dataset\_id}/admin/retention-policy>

{
  
    "type": "expire\_when",  
  
    "expression": {  
  
       "type": "snapshot\_age",  
  
       "operator": ">",  
  
       "period": "P30D"  
  
      }  
}

The dataset's response json will have a subsection that look similar to the following:

"name": "Dataset Name",  
  
     "retention\_policy": {  
  
        "type": "expire\_when",  
  
        "expression": {  
  
        "type": "snapshot\_age",  
  
        "operator": ">",  
  
        "period": "P30D"  
  
        }  
}

Once a dataset's retention policy is in place, buyers and sellers can call the following endpoint to understand which snapshots from their dataset are set to expire:

<https://api.narrative.io/datasets/932/retention-policy/preview>

The response will contain an array of relevant snapshots:

{  
  
"snapshots\_to\_expire": \[\]  
  
}

#### Dataset Statistics

Dataset statistics provide insights into the size and counts of a single dataset. Providers want to know how much data is in their dataset to:

1. Audit that their ingestion is working as expected
2. Understand how the current state of the dataset is contributing to their storage costs
3. View insights into the distribution of values behind their dataset

Narrative solves all three of these use cases by pulling the history of dataset statistics through individual snapshots. The change in row counts (rows added or deleted) are captured in the delta between snapshots. For example, snapshot one was captured on Tuesday and indicates that a dataset has 2000 rows. Snapshot two was captured on Wednesday and indicates that a dataset has 3000 rows. The user can infer that 1000 rows were added between Tuesday and Wednesday. This system of record is how Narrative calculates a user's dataset storage costs over time.

A union of all the files listed in the manifest of each snapshot, while filtering out the files that are deleted, gives a holistic view of a dataset's history. Users can pull dataset statistics by calling the following endpoint: <https://api.narrative.io/datasets/{dataset\_id}/stats>

The response will look similar to the following depending on a dataset's schema and row counts:

{  
    "dataset\_id": xxx,  
    "records":  
    \[  
        {  
            "snapshot\_id": 8116371869825870170,         # snapshot\_id  
            "total\_dataset\_files": 924178,                # total\_table\_files  
            "total\_dataset\_records": 3392852797,        # total\_table\_records  
            "snapshot\_added\_files": 2,                    # snapshot\_added\_files  
            "snapshot\_added\_records": 203023,            # snapshot\_added\_records  
            "snapshot\_deleted\_files": 0,                # snapshot\_deleted\_files  
            "snapshot\_deleted\_records": 0,                # snapshot\_deleted\_records  
            "active\_dataset\_stored\_bytes": 410850194493,# total\_table\_size\_in\_bytes  
            "est\_dataset\_stored\_files": 924178,            # estimated\_total\_table\_files  
            "snapshot\_added\_deleted\_files": 0,            # snapshot\_added\_delete\_files  
            "snapshot\_added\_stored\_bytes": 17048471,    # snapshot\_added\_size\_in\_bytes  
            "est\_dataset\_stored\_records": 3392852797,    # estimated\_total\_table\_records  
            "snapshot\_removed\_deleted\_files": 0,        # snapshot\_removed\_delete\_files  
            "snapshot\_removed\_bytes": 0,                # snapshot\_removed\_size\_in\_bytes  
            "est\_dataset\_total\_stored\_bytes": 410850194493 # estimated\_total\_table\_size\_in\_bytes,  
            "columns\_summary": \[  
                {  
                    "name": "unique\_id",    # name  
                    "type": "string",        # type  
                    "nanValue": "NaN",        # nanValue  
                    "nullValue": "",        # nullValue  
                    "valueCount": 3000,        # valueCount  
                    "columnSizes": 30323,    # columnSizes  
                    "lower\_bounds": true,    #lowerBounds  
                    "upper\_bounds": false  
                }  
  
            \]  
        }  
    \]  
}
