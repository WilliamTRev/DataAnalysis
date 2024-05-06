[Looker Standard and Looker Studio Comparison](https://cloud.google.com/looker/docs)

# Looker Standard

Looker may be managed for you in Google Cloud, hosted by you in another cloud service, or hosted on your own servers. In each case data always remains in-database and is not copied to the Looker instance.

- Governance for key metric definitions
- Robust data access permissions
- Sharing, scheduling, and alerting
- Operational analytics
- Integration of analytics in existing tools and workflows
- Custom applications

# Looker Studio

Looker Studio is a Google Cloud service that is available at lookerstudio.google.com to anyone with a Google account.

- Self-service analytics and visualizations
- Interactive dashboards to more than 1,000 data sources
- Report embedding for the web
- One-off visualizations or reports
- Single data source or pre-aggregated datasets

1. [access Looker Studio](https://lookerstudio.google.com/)

2. [Functional References in Looker Studio](https://support.google.com/looker-studio/topic/7019880?hl=en&ref_topic=7570421&sjid=10918353975172379725-NA)
- also [Functional References in Looker Studio](https://blog.coupler.io/looker-studio-formulas-and-functions/)

- [video on functions in looker Studio](https://support.google.com/looker-studio/answer/6299685?sjid=10918353975172379725-NA#zippy=%2Cin-this-article)

3. [Calculated Field With Parameter Example](https://support.google.com/looker-studio/answer/9002005#create-a-parameter&zippy=%2Cin-this-article%2Ccalculated-field-with-parameter-example)

- and the best reference is here, please explore:
4. [Looker Studio docs](https://developers.google.com/looker-studio)

# Looker Standard
An **Explore** is a starting point for a query that is designed to explore a particular subject area. Select the Explore option from the left navigation panel to open the Explore menu.See [explores](https://cloud.google.com/looker/docs/creating-and-editing-explores). Explores contain views, which are groupings of dimensions and measures.

The Explore menu presents a number of descriptive model or group names that are organized in alphanumeric order. From the Explore menu, you can search for and select Explores, which are organized alphanumerically under the model or group name to which they belong.

Looker **Measures** are an aggregation of one or more dimensions (or unique attributes of the data). Measures let you calculate your Key Performance Indicators (KPIs) and help you analyze your data using different attributes.

**Dimensions** are unique attributes of the data that helps you describe the data. You can use both Dimensions and Measures in Looker to slice and dice your data to achieve data insights.

## Merged Results
Explores in Looker are designed by your Looker developers to combine the data from your database tables in the best way, using defined relationships between data fields and tables. Because of this, it is best to use a single Explore to examine your data.

However, there may be times when your Looker developers haven’t created the relationships you need, or they faced technical limitations. In these cases, Looker lets you combine data from different Explores (even from different models or projects) to create data tables and visualizations.

Using the Merged Results feature, you can create a query from an Explore and then add queries from other Explores to display the merged results in a single table. From there, you can examine the data, pivot fields, and create visualizations.

By default, that first query is considered the primary query. This is an important concept because when Looker matches the data to create the merged results, it matches each added query to the primary query (not to any other added query).

So, whenever you add a query, you need to include a dimension that can be matched to a dimension in the primary query.

Learn more about merged results from the [Merging results from different Explores documentation](https://docs.looker.com/exploring-data/exploring-data/merged-results#understanding_merged_results).

## Modeled Query

**Modeled queries** are created from the **[query parameter](https://cloud.google.com/looker/docs/reference/param-explore-query)** in LookML. The modeled analyses are listed in the Quick Start section of a blank Explore, or in the Quick Start pop-up after an Explore has already been run. Quick Start analyses provide a helpful starting point for users to quickly explore the meaningful data and build reports.

Common use cases
- Demonstrating the power of Explores to highlight key types of analyses that can be created from a specific Explore page.
- Offering a "soft-landing" for new explorers that are initially less intimidating and allow them to tweak an existing analysis vs. building one entirely from scratch.
- Saving time for seasoned users by modeling frequent queries and using them as Quick Starts to make your analyses faster and less repetitive, just like modeling commonly requested fields in LookML reaps benefits in terms of reusability .
- Providing one-click access to common filter sets by providing explorers with a preconfigured set of filters to grab and go. No need to repetitively add and configure the ones you need.

How to create a query parameter:
The query parameter includes a list of subparameters that you can define in a LookML model. The easiest way to define a query in your model is by building the analysis in an Explore, borrowing the functionality used to generate aggregate_table LookML and then copying the aggregate table LookML to use as a starting point for your modeled analysis LookML.

Instead of creating the query's LookML from scratch, you can use an Explore to create the query's base LookML for you. 

The query parameter has the following subparameters:

| Parameter  Name |	Description |	Example |
|-------|-------------------------------|------------|
|label	| Optionally, adds a label for the query. The label is what is displayed in the Explore's field picker for the query.	| label: "Weekly Sales Totals"
|description	| Optionally, adds a description about this query to inform your users. In the Explore, any queries with a description will have an information icon. The description text is displayed when a user hovers over the information icon.|	description: "Total value of all sales per day"
|dimensions	| A comma-separated list of the dimensions from the Explore to be included in your query. The dimensions field uses this syntax: dimensions: [dimension1, dimension2, ...]|	dimensions: [orders.created_month, orders.country] |
|measures |	A comma-separated list of the measures from the Explore to be included in your query. The measures field uses this syntax: measures: [measure1, measure2, ...]	|measures:   [orders.count] |
| filters |	Optionally, adds filters to a query. Filters are added to the WHERE clause of the SQL that generates the query. The filters field uses this syntax: filters: [field_name_1: "value1", field_name_2: "value2", ...]	| filters: [orders.country: "United States", orders.state: "California"]|
|limit	| Optionally, specifies the row limit of the query.	| limit: 10 |
| sorts |	Optionally, specifies sort fields and sort direction (ascending or descending) for the query. The sorts field uses this syntax: sorts: [field1: asc &#124; desc, field2: asc &#124; desc, ...] |	sorts: [order_items.total_sales: asc] |
|pivots	| Optionally, pivots the results on the specified dimensions of the query. The pivots field uses this syntax: pivots: [dimension1, dimension2, ...] NOTE: The fields specified in the pivots parameter must also be specified in the dimensions parameter of the query.	| pivots: [created_quarter] |
|timezone	| NOT SUPPORTED The timezone parameter is not supported for the query parameter that is a subparameter of explore. A query under explore uses the same time zone used by the explore.|	

More helpful documentation:
- [LookML query parameter](https://docs.looker.com/reference/explore-params/query)
- [Exploring data in Looker](https://docs.looker.com/exploring-data/exploring-data)

### Pivot Dimensions
Multiple dimensions are often easier to look at when you pivot one of the dimensions horizontally. Each value in the dimension will become a column in your Look. This makes the information easier to consume visually, and reduces the need to scroll down to find data.

### Reorder columns and remove fields
You can reorder columns in the Data section by clicking on a column header and moving the column to its desired position. The Explore's visualization will reflect the new column order after you click Run.

Columns are organized in the Data section by field type: 
- dimensions
- [dimension table calculations](https://docs.looker.com/exploring-data/using-table-calculations) 
- measures
- [measure table calculations](https://docs.looker.com/exploring-data/using-table-calculations)
- [row totals](https://docs.looker.com/exploring-data/exploring-data#displaying_totals)

### Table Calculations
Table calculations make it easy to create on-the-fly metrics. They are similar to formulas found in spreadsheet tools like Excel. Table calculations appear as green columns in the data table, rather than as blue columns (dimensions) or orange columns (measures).

Table calculations can perform mathematical, logical (true/false), lexical (text-based), and date-based calculations on the dimensions, measures, and other table calculations in your query. The formulas that you use to execute these calculations are called [Looker expressions](https://docs.looker.com/exploring-data/creating-looker-expressions).

Table calculations are different from regular fields
Although table calculations are similar to dimensions and measures, there are some important differences:

- Table calculations give anyone the ability to create new fields, as opposed to regular fields, which require that you have development permissions and understand LookML.
- Table calculations operate on the results from your query, as opposed to regular fields, which are part of the query itself. In other words, you will select a set of dimensions and measures and run your report as normal, then you can base table calculations on the data in that report.
- Although table calculations are easier to create than regular fields, they are not as easily controlled as regular fields. Since they can be created by anyone within your organization, they might not be the "official" calculations. Keep this tradeoff in mind as you decide between regular fields and table calculations, since one of the key advantages of Looker is having a single source of truth!

#### Looker Expressions

[Looker expressions](https://docs.looker.com/exploring-data/creating-looker-expressions) (sometimes referred to as Lexp) are used to perform calculations for:

- [Table calculations](https://docs.looker.com/exploring-data/using-table-calculations) (which include expressions used in [data tests](https://docs.looker.com/reference/model-params/test))
- [Custom fields](https://docs.looker.com/exploring-data/adding-fields/custom-measure)
- [Custom filters](https://docs.looker.com/exploring-data/filtering-and-limiting#custom-filters)
A major part of these expressions is the functions and operators that you can use in them. The functions and operators can be divided into a few basic categories:

- [Mathematical](https://docs.looker.com/exploring-data/creating-looker-expressions/looker-functions-and-operators#math): Number-related functions
- [String](https://docs.looker.com/exploring-data/creating-looker-expressions/looker-functions-and-operators#string): Word- and letter-related functions
- [Dates](https://docs.looker.com/exploring-data/creating-looker-expressions/looker-functions-and-operators#date): Date- and time-related functions
- [Logical](https://docs.looker.com/exploring-data/creating-looker-expressions/looker-functions-and-operators#positional) transformation: Includes boolean (true or false) functions and comparison operators
- [Positional transformation](https://docs.looker.com/exploring-data/creating-looker-expressions/looker-functions-and-operators#positional): Retrieving values from different rows or pivots

Some functions are only available for table calculations
Looker expressions for [custom filters](https://docs.looker.com/exploring-data/filtering-and-limiting#custom-filters) and [custom fields](https://docs.looker.com/exploring-data/adding-fields/custom-measure) do not support Looker functions that convert datatypes, aggregate data from multiple rows, or refer to other rows or pivot columns. These functions are supported only for [table calculations](https://docs.looker.com/exploring-data/using-table-calculations) (including table calculations used in the expression parameter of a data test).

The [Looker functions and operators documentation](https://docs.looker.com/exploring-data/creating-looker-expressions/looker-functions-and-operators) is organized to clarify which functions and operators are available, depending on where you are using your Looker expression.


## LookML
LookML (Looker Modeling Language) generates abstracted SQL and provides a modeling layer between the database and user. It is Looker's proprietary language that provides an abstraction layer for SQL databases.

Specifically, LookML is a language for describing dimensions, aggregates, calculations, and data relationships in a SQL database. Looker uses a model written in LookML to construct SQL queries against a particular database. It creates the layer between that SQL database and how the business user interacts with it.

As such, it defines many different things, like how to join tables, how to define custom tables, how to define fields from the database, and the logic for new fields. In this lab, you will get hands-on experience with the fundamentals of LookML.

The hierarchy of LookML is structured using the following objects:

- Projects, which are libraries of LookML code. Because Looker uses Git for version control, a best practice is for each project to map 1:1 with a Git repository.
    A project is composed of one or more models.
    
- A model is a set of Explores by business area or need. An Explore is a set of pre-joined views for business-user analysis.
    Each model contains one or more Explores.
    
- A view in LookML is a database table or a logical representation of one.
    Each view includes dimensions (which are database columns or logical representations of them) and measures (which are aggregate functions on dimensions, such as a COUNT of customers or a SUM of cost).


### Projects
The highest-level LookML object is the project. A project is essentially a library of code that typically maps 1:1 to a data source or database connection. You can think of each project as an almost independent mini-instance or microcosm of Looker.

Schemas that cannot be joined together usually reside in different projects because there is no relation to be made across the two datasets. This depends on your database dialect and database user permissions.

A key concept to remember is: if it's possible in your SQL dialect, it should be possible in Looker. If you can go to your database console and hand-write a SELECT statement that does a thing, you can also code LookML so that Looker does the same thing.

LookML Projects table with a list of project names and their associated models

You can share content from one project to another via a feature called Project Import, if necessary, and if it's enabled for your instance, but this is an advanced approach to setting up your model architecture and not in the scope of this lab.

### Models
Models are the next level of hierarchy and contain:

Models contain data connection information and definitions of Explores. Models can be used to restrict user access to certain Explores and separate and organize Explores by business area.

### Explores
Explores are one or more views joined together, usually to target a specific business question. Explores should be organized around business themes to minimize confusion for users.

Explores are the "drivers" of analysis on the frontend. They include one or more views joined together, and each usually targets a specific business question. Think of an Explore as a predefined set of tables that would frequently be joined for business inquiries and use cases.

### Views
Views are where you define dimensions (which are the data attributes) and measures (which are aggregations of dimensions). Think of views as tables that bundle related fields. There are a few different types of views:

- Standard views, which abstract what's already in the database tables.
- Virtual tables, known as derived tables.


### Dimensions
The lowest level of a LookML object are fields, which can be dimensions or measures. Dimensions are created for any columns that are already in your database tables when the view files are generated from a table by Looker.

You can also create additional dimensions that would serve as logical representations of table columns. These appear in the SELECT and GROUP BY clause of a SQL statement. They are the "attributes" that describe your data.

### Measures
Measures are aggregates that do not live explicitly in your database tables. They must be created in LookML. They aggregate dimensions into values like sums or counts.

Note that they do not appear in the GROUP BY statement of the SQL generated by Looker. Instead, they depend on dimensions to determine that grouping.

measure highlighted in the users.view view

To recap, a project is a library of code that models a data source and should map 1:1 to a Git repository. Projects contain:

- Model files, which define the Explores that should be packaged together and how those Explores work.
- View files, which describe database tables or logical representations of them.
Dimensions and measures are defined within view files.

Projects can also include dashboards defined in LookML to prevent business users from editing them, maintain version control, and sync them across Looker instances if your company has more than one. LookML dashboards are not in the scope of this training.

There are other types of project files, such as documents and manifests. If you're interested, you can refer to the [Understanding other project files documentation](https://docs.looker.com/data-modeling/getting-started/other-project-files).

#### More References
[LookML quick reference](https://docs.looker.com/reference/lookml-quick-reference)
[LookML terms and concepts](https://docs.looker.com/data-modeling/learning-lookml/lookml-terms-and-concepts)
[Join the Looker Community](https://community.looker.com/)
[Additional LookML basics](https://docs.looker.com/data-modeling/learning-lookml/advanced-lookml-concepts)

## Looker Standard Labs
- [Looker Data Explorer - Qwik Start](https://www.cloudskillsboost.google/catalog_lab/3509)
- [Filtering and Sorting Data in Looker](https://www.cloudskillsboost.google/catalog_lab/3557)
- [Merging Results from Different Explores in Looker](https://www.cloudskillsboost.google/catalog_lab/3640)
- [Creating a Looker Modeled Query and Working with Quick Start](https://www.cloudskillsboost.google/catalog_lab/4137)
- [Looker Functions and Operators](https://www.cloudskillsboost.google/catalog_lab/3635)
- [Exploring Data with Looker: Challenge Lab](https://www.cloudskillsboost.google/catalog_lab/3679)
- [Looker Developer - Qwik Start](https://www.cloudskillsboost.google/catalog_lab/3838)
- [Creating Measures and Dimensions Using LookML](https://www.cloudskillsboost.google/catalog_lab/3837)
- [Creating Derived Tables Using LookML](https://www.cloudskillsboost.google/catalog_lab/3836)
- [Filtering Explores with LookML](https://www.cloudskillsboost.google/catalog_lab/3839)
- [Caching and Datagroups with LookML](https://www.cloudskillsboost.google/catalog_lab/3840)

## Looker Studio Labs
- [Explore and Create Reports with Looker Studio](https://www.cloudskillsboost.google/catalog_lab/1450)
- [How to Build a BI Dashboard Using Google Looker Studio and BigQuery](https://www.cloudskillsboost.google/catalog_lab/1738)
- [Looker Studio: Qwik Start](https://www.cloudskillsboost.google/catalog_lab/768)
- [Get Started with Looker: Challenge Lab](https://www.cloudskillsboost.google/catalog_lab/6266)
- [Get Started with Looker](https://www.cloudskillsboost.google/course_templates/647)


