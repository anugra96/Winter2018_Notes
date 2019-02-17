# Lecture 10

## Database Design

### Criteria of a good design

- correctness
- completeness
- minimum redundancies
  - tables link with foreign keys
    - if you change one table, then all linked tables will change too
  - **redundancy: ** not only about space, but also the probability of inconsistency when making changes



## Data Warehouse

- large scale database, designed specifically for large scaled complex data analysis
- data in DW is usually copied from the smaller database (operational database)
- data is integrated from different databases
- data is organized based on business subjects