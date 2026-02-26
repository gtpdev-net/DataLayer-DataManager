# Data Layer - Data Manager

## Mission

The Data Manager is an ASP.NET Core 8 Blazor Web Application designed to orchestrate and manage complex data migration projects. It enables organizations to extract source database schemas, define migration rules, and automatically generate the Entity Framework code necessary to implement dual-model (Relational and Document) data architectures.

## Overview

The application guides users through a structured migration workflow:

1. **Source Schema Extraction** – Extract and store database schema information from DACPAC files
2. **Migration Mapping** – Define which data points migrate and to which target model(s)
3. **Target Schema Generation** – Automatically generate the required Entity Framework configuration
4. **Data Migration** – Extract data from the source database and load it into the target

## Key Capabilities

### Source Database Schema Management
- Import DACPAC files to extract complete database schema information using the DacFx package
- Persist source schema metadata in an Azure SQL Server database using Entity Framework with FluentAPI configuration
- Browse source schema in a searchable, sortable, and filterable table with robust column selection
- Maintain schema integrity by restricting modifications to DACPAC re-imports

### Migration Rule Definition
The Data Manager captures migration directives at the data-point level:
- Identify which source entities and properties (tables and columns) participate in migration
- Specify target destination(s): Relational Model (SQL), Document Model (NoSQL), or both
- Construct a comprehensive migration map that defines the data distribution across SQL and NoSQL stores

### Entity Framework Code Generation
Automatically generate all necessary Entity Framework components based on the target schema:
- Entity classes
- DbContext configurations
- FluentAPI schema definitions
- Repository and Service interfaces

Generated artifacts are deployed to configurable output locations

### Data Migration
Automates the extraction and loading of data from a configured source database to target destinations:
- Extract relevant relational data from the source database
- Generate corresponding Document pairs for extracted records
- Load relational data into the target Azure SQL database
- Load prepared JSON Document pairs into the target Cosmos DB container
- Monitor progress in real-time via an interactive dashboard