# dbt-databricks-data-engineering-project

**Seeds:**
seeds are meant for small,static datasets-not a replacement for a proper EL(extract/load) pipeline 
if the data does not exist in any source system, you can:
    1.put it in a .csv file in your /seeds folder.
    2.run dbt seed to load it into your warehouse as a table.
    
**Good fit**: mapping tables, config values, manual reference data, test fixtures

**Not a good fit**: transactional data, large datasets, frequently updated data — for those, use a proper ingestion tool (Fivetran, Airbyte, Azure Data Factory, etc.) and define them as sources in dbt.


**snapshots**:
Snapshots in dbt implement Slowly Changing Dimensions (SCD Type 2) — they track how rows in a source table change over time.

**How it works:**
    1.dbt takes a "snapshot" of your source data each time you run dbt snapshot
    2.When a row changes, dbt doesn't overwrite it — it marks the old row as invalid and inserts a new row with the updated values
    3.Each row gets metadata columns: dbt_valid_from, dbt_valid_to, and dbt_updated_at
