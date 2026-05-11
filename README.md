# dbt-databricks-data-engineering-project

**Seeds:**
seeds are meant for small,static datasets-not a replacement for a proper EL(extract/load) pipeline 
if the data does not exist in any source system, you can:
    1.put it in a .csv file in your /seeds folder.
    2.run dbt seed to load it into your warehouse as a table.
    
**Good fit**: mapping tables, config values, manual reference data, test fixtures

**Not a good fit**: transactional data, large datasets, frequently updated data — for those, use a proper ingestion tool (Fivetran, Airbyte, Azure Data Factory, etc.) and define them as sources in dbt.
