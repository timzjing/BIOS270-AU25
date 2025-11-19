# Write-up 3

**Name:** Tim Jing
**Student ID:** timjing
**Date:** 11/18/2025  

---

## Overview

This writeup covers data.md.

---

## Content

#### Data.md

1. There is only one .gff file according to the description (`genomic.gff`), so there will be one table created in the database.

2. The try-except clause is necessary to prevent catatsrophic failure when the .to_sql function fails. This can occur for a variety of reasons, such as if there are concurrent writes to the same database. This ensures accurate updates to the database.

3. Unable to complete `query_bacterai_db.py` due to improper permissions.

4. Chunk size breaks down the large database into more manageable sections for uploading to BigQuery. Otherwise, processing all rows at once might be too challenging.

5. The chunk configuration makes sense becuase it accesses a certain chunk of rows, with all of the features included in the columns. This makes sense because our data is stored in a row-based manner, where each entry takes one row. This is common in biological use cases where individual samples, patients, etc. are in each row.


## Acknowledgement
Collaborator: N/A
