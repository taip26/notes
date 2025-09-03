# Palantir Foundry Platform

Data-oriented platform

Used to create pipelines to transform and move data
 - light pipelines are faster 
 - streaming pipelines are for continous data

## E2E Speedrun
### Pipeline
1. Create project + file
2. upload datasets
3. clean both of the csv
 - click (or right click?) on bro and select the blue 3-line triangle icon for transform
4. Join tables with consolidated_customers table
5. Union joined tables for final one-order-table
6. Output union to new dataset
 - can remove columns in this step if desired
7. Deploy pipeline
 - save -> deploy -> deploy pipeline

### Ontology
1. Create new ontology manager
2. set order id as primary key and item name as title (display name)

### Workshop Application
1. Create workshop under ontology manager dependents
2. Add object table to widget
3. Add object set to object table
4. Create a filter set and add filters for every table col, using multi-select when possible
5. Create a variable using the object set and filter that was just created
6. Create details page for each object
 - Object set title
 - button group
 - property list

