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

5. [Looker Studio Chart Reference](https://support.google.com/looker-studio/topic/7059081?hl=en&ref_topic=9207420&sjid=8055637326223498048-NA)

# Looker Standard
An **Explore** is a starting point for a query that is designed to explore a particular subject area. Select the Explore option from the left navigation panel to open the Explore menu.See [explores](https://cloud.google.com/looker/docs/creating-and-editing-explores). Explores contain views, which are groupings of dimensions and measures.

The Explore menu presents a number of descriptive model or group names that are organized in alphanumeric order. From the Explore menu, you can search for and select Explores, which are organized alphanumerically under the model or group name to which they belong.

Looker **Measures** are an aggregation of one or more dimensions (or unique attributes of the data). Measures let you calculate your Key Performance Indicators (KPIs) and help you analyze your data using different attributes.

**Dimensions** are unique attributes of the data that helps you describe the data. You can use both Dimensions and Measures in Looker to slice and dice your data to achieve data insights.

## Dimensions
In Looker, a dimension is a group-able field and can be used to filter query results. It can be:

- An attribute, which has a direct association to a column in an underlying table
- A fact or numerical value
- A derived value, computed based on the values of other fields in a single row
For example, dimensions for a Products view might include product name, product model, product color, product price, product created date, and product end-of-life date.

Dimensions let you create buckets of data points to analyze your KPIs using different attributes. You can create different types of dimensions like time, numeric, yesno and string to slice and dice your data. For dimension types refer to [dimension types](https://docs.looker.com/reference/field-reference/dimension-type-reference).

## Measures
A measure is a field that uses a SQL aggregate function, such as COUNT, SUM, AVG, MIN, or MAX. Any field computed based on the values of other measure values is also a measure. Measures can be used to filter grouped values. For example, measures for a Sales view might include total items sold (a count), total sale price (a sum), and average sale price (an average).

The behavior and expected values for a field depend on its declared type, such as string, number, or time. For measures, types include aggregate functions, such as sum and percent_of_previous. For details, refer to  [measure types](https://docs.looker.com/reference/field-reference/measure-type-reference).

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
The lowest level of a LookML object are fields, which can be dimensions or measures. Dimensions are created for any columns that are already in your database tables when the view files are generated from a table by Looker. You can also create additional dimensions that would serve as logical representations of table columns. These appear in the SELECT and GROUP BY clause of a SQL statement. They are the "attributes" that describe your data.

### Measures
Measures are aggregates that do not live explicitly in your database tables. They must be created in LookML. They aggregate dimensions into values like sums or counts. Note that they do not appear in the GROUP BY statement of the SQL generated by Looker. Instead, they depend on dimensions to determine that grouping.

To recap, a project is a library of code that models a data source and should map 1:1 to a Git repository. Projects contain:

- Model files, which define the Explores that should be packaged together and how those Explores work.
- View files, which describe database tables or logical representations of them.
Dimensions and measures are defined within view files.

Projects can also include dashboards defined in LookML to prevent business users from editing them, maintain version control, and sync them across Looker instances if your company has more than one. LookML dashboards are not in the scope of this training.

There are other types of project files, such as documents and manifests. If you're interested, you can refer to the [Understanding other project files documentation](https://docs.looker.com/data-modeling/getting-started/other-project-files).

## Explore Filters with LookML
To filter an Explore, you need to apply a default WHERE or HAVING clause to every SQL query that gets generated in that Explore. There are three principal ways to filter an Explore:

- **sql_always_where** and **sql_always_having**, which behave similarly and have the same use case
- **always_filter**
- **conditionally_filter**


### The sql_always_where and sql_always_having filters
Both sql_always_where and sql_always_having allow you to add filters to an Explore that cannot be modified. This is useful when you have certain rows of data you always want to exclude from the Explore results.

The sql_always_where filter is used to add a WHERE clause applied to dimensions in a SQL query, whereas sql_always_having is used to add a HAVING clause applied to measures in a SQL query. In addition to queries run explicitly by business users, the restriction will apply to dashboards, scheduled Looks, and embedded information that relies on that Explore.

There will be no indication of the filter in the user interface, so business users are not informed that the data are being filtered, unless they have permission to look at the generated SQL. This is useful if you want to filter out certain values of the Explore, such as test or internal data.

### The always_filter
The always_filter enables you to require users to include a certain set of filters that you define. You also define a default value for the filters. Though users may change your default value for their query, they cannot remove the filter entirely. This is helpful when you want users to always filter by specific dimensions, such as always filtering by order status or user country, so that they do not request all of the possible data at one time.

The always_filter has a sub-parameter to define the specific filters using the same Looker filter expressions that are used to filter dimensions and measures. The dimensions provided in the filters sub-parameter identify the dimensions that users must provide values for, such as a value for order status or user country.

The specific values provided for in the filters sub-parameter are the default values which can be changed by the business user. For example, while the default order status is "Complete", business users can change this value to say orders with a different status like "Returned". For additional information, review the [Looker filter expressions document](https://docs.looker.com/reference/filter-expressions).

### The conditionally_filter
Similar to the always_filter, the conditionally_filter adds a filter to the Explore frontend that is accessible by business users. The conditionally_filter parameter enables you to define a set of default filters that users can override if they apply at least one filter from a second list that you define.

Although users can indeed change the filter operator and values, they cannot remove the filter itself unless they put a filter on a specific alternative field. This is helpful when you want to limit the amount of data that an business user requests, but you also want to give them a list of alternative dimensions that they can use to filter the data.

Conditionally_filter has a sub-parameter to define the specific filters as well as a sub-parameter to define the alternative dimensions that can be used to filter the data. For example, conditionally_filter can be used to create a filter that only returns data for the past 1 year, unless a filter is applied to a user ID or state dimension. This is typically used to prevent users from accidentally creating very large queries that may be too expensive to run on your database.

## LookML Validator
The [LookML Validator](https://docs.looker.com/data-modeling/getting-started/lookml-validation#validating_your_lookml) is used to perform a full model validation. Some errors, such as an invalid field reference due to a missing join, require a holistic look at the model and therefore are only surfaced when the LookML Validator is run. The LookML Validator checks all of the LookML code in a model, such as the syntax of object definitions (for example, dimensions and measures) and defined relationships (for example, joins). However, it does not check the SQL parameters of LookML objects (for example, SQL derived tables).

## Caching and Datagroups with LookML

Looker is constantly generating SQL queries and sending them to the connected database. Whenever someone runs a query in Looker, the SQL results are cached and stored in an encrypted file on the Looker instance. Caching leverages the saved results from previously executed queries so that the same query is not run on the database repeatedly. This helps reduce database load. Caching also helps optimize Looker performance. In this lab, you learn how caching works in Looker and explore how to use LookML datagroups to define caching policies.

### The caching process
Looker acts like a front door attendant for a database. When a user runs a query, Looker determines whether the exact same query has been run before. If not, it allows the query to run on the database. When the results are returned, Looker caches them for future reference. If the same query has been run before, Looker checks the caching policy to determine whether the results are still valid. If yes, Looker returns the cached results to the business user. This happens in less than a second. If the same query has been run before but the results are no longer valid per the caching policy, Looker sends the query to the database. It then caches the new results for future reference.

### Datagroups
A datagroup is the Looker term for a named caching policy or rule. LookML developers use datagroups to manage caching on a Looker instance. Different caching policies require separate datagroup definitions. The number and types of datagroups you need to create depends on your data's extraction, transformation, and loading (ETL) processes and business requirements.

For example, you may need to define datagroups at the model level, for individual Explores, or for persistent derived tables (PDTs), depending on how often your data is updated.

- To apply a datagroup as the default for all Explores, use the persist_with parameter at the model level.
- To apply a datagroup to a specific Explore, use the persist_with parameter in that Explore's definition.
- To apply a datagroup to a specific set of Explores but not all Explores in a model, use the persist_with parameter in each Explore's definition and specify the same datagroup name.

#### Objects that can use datagroups:
##### **Persist_with**
If you apply a datagroup at the model level, Looker, by default, will apply the same caching rules to all Explores within this model.

However, you can apply a datagroup on an individual Explore, which overrides any setting at the model level. Because Explores are the foundation for all content, the same caching logic applies to Looks and dashboards in the Explore.

#### **datagroup_trigger**
For PDTs, you can apply a datagroup to specify how the PDT is rebuilt.

#### **schedules**
Schedules for Looks and dashboards can also be run on datagroups. You can instruct Looker to run a Look or dashboard automatically upon expiration of a caching policy, so new data is retrieved and "pre-cached" for any business users who need it.

### Datagroup configuration
Datagroups take two parameters: **max_cache_age** and **sql_trigger**.

- max_cache_age specifies the number of hours to keep a cached result, such as 24 hours.
- sql_trigger is used to write a SELECT statement that can tell Looker whether the results have changed. The sql_trigger should be written to return only one value. Looker will regularly send this statement to the connected database. If the result has changed, Looker refreshes the cache.

Although only one parameter is required, it is best to use both to achieve the desired caching results. For example, if the sql_trigger check doesn't detect a change, that could mean something went wrong with the ETL process or the sql_trigger itself. If you include a max_cache_age parameter, the cache will be refreshed after a set duration regardless of the result of the sql_trigger check.

## Running queries in the Explore
After defining new LookML objects, you can run queries in the Explore. This helps troubleshoot your LookML code because it displays SQL errors provided by the underlying database (for example, inadequate permissions, incorrect SQL object references, or invalid aggregations).

## SQL Runner
[SQL Runner](https://docs.looker.com/data-modeling/learning-lookml/sql-runner-create-queries#debugging_using_sql_runner) provides a way to directly access your database and is also a useful tool for checking SQL errors in queries. This is where you can test the custom SQL that you want to include within SQL parameters of LookML objects. You can also see a list of database tables, run ad hoc queries, write queries for SQL derived tables, etc.

## Content Validator
The [Content Validator](https://docs.looker.com/data-modeling/getting-started/look-validation#using_the_content_validator_to_fix_errors) validates all references that your Looks and dashboards make to your LookML models, Explores, views, and fields, and displays an error for any references your content makes to an unknown LookML object. It also checks the Looks and dashboards that were created in the instance to ensure that their references to LookML objects are valid (for example, the name of a specific dimension or measure the Explore might have changed over time).

[The Looker error catalog](https://docs.looker.com/reference/looker-error-catalog) provides a list of common error messages, their underlying causes, and where in Looker the message is displayed.

## Derived Tables
In LookML, you can define derived tables using either SQL queries to define a **SQL derived table** or Explore queries to define a native derived table.

In contrast to SQL derived tables, **native derived tables**, or NDTs, are expressed entirely in LookML. Native derived tables are useful because they embody that essential LookML principle of reusability. They allow you to inherit already existing dimensions, measures, and even Explores and join logic. Since you’re minimizing the number of "hard-coded" database references, this makes your code much more maintainable in the long run.

The native derived table is considered ephemeral because it is generated at run-time as a CTE, rather than stored in the underlying database. Derived tables can also be persisted, which means that they are stored in the underlying database. For more information on persistent derived tables, review [Creating persistent derived tables (PDTs) documentation](https://docs.looker.com/data-modeling/learning-lookml/derived-tables#creating_persistent_derived_tables).

The steps to persist a derived table are the same whether it is a SQL derived or native derived table.

As mentioned previously, the benefit in persisting derived tables is that they are ready to go when business users need them, and therefore reduce query runtimes. The downsides are that they take up storage space in your database (which may correlate to cost), and they are more rigid. To persist a derived table, you must use one or two of these parameters in the definition:

- **datagroup_trigger** uses a datagroup, or caching policy configured in the model. If datagroups are defined in the model, then this is the best practice for persisting derived tables.
- **sql_trigger_value** uses a pre-written SELECT statement that returns one value. Looker sends that SELECT statement to the database repeatedly, and when it discovers the result has changed, it takes this as a cue to rebuild the PDT.
- **persist_for** instructs the PDT to stay up for a set duration, such as "1 hour" or "4 hours".
However, it is important to note that persist_for does not have any rebuild logic, so the PDT would not get updated during that time. In addition, once time is up, the PDT is dropped, and it doesn’t come back until a business user needs it for a query.

Because the primary benefit of PDTs is having data readily available to minimize query runtimes, it is recommended that you use persist_for in conjunction with sql_trigger_value to ensure that data updates are captured in the PDT, or simply use datagroup_trigger or sql_trigger_value.

## LookML Extends
Extends allow you to modularize code by creating copies of LookML objects that can then be integrated into other LookML objects and modified independently from the original LookML object. In Looker, you can extend views, Explores, and LookML-defined dashboards. By modularizing your code, extends allow you to treat pieces of code as modules or units that you can then build upon to expand your model.

Why use extends?
- writing DRY (Don't Repeat Yourself) code
- easier/faster to make changes
- consistency
- easier management of different field sets

Extends help you write D.R.Y. (Don't Repeat Yourself) code. By copying preexisting objects and sections of code, you can more easily add or modify logic. This is critical for scaling your model as your organization and use cases expand. It also maximizes consistency in your model, because you aren't manually rewriting code all the time. And it makes it easier to manage field access for different groups of users, which is also important for scalability.

### LookML view extends
As mentioned earlier, one object you can extend is a LookML view. This is commonly done to add more fields and/or update logic to the existing fields. Another use case is to change the database table specified in the sql_table_name parameter.

#### Extend a view to add columns from another view
Instead of copying/pasting the same code across multiple views, you can create one centralized view that contains definitions for commonly used dimensions and measures. Then, using extends, you can integrate those dimensions and measures into multiple views. You can simply use specific parameters for extends to identify the view that you want Looker to copy from.

From a business perspective, this is very practical because you can have one centralized code base that is reused by multiple teams that can extend the core code and customize it for their own needs. The benefit of abstracting the location dimensions is that you can update them once, and the update is then propagated to any of the views that are extended from that location view.

### LookML Explore extends
Another object you can extend is Explores. You may have multiple tables that must always be joined together, especially in a more normalized database architecture. To avoid rewriting the same joins repeatedly, you can make a “base” Explore that already joins them together and then extend it to create additional Explores that need to join in more views. Or you may need the same set of joined views, but with the new Explore starting from a different base view.

The four steps involved in Extend execution
Steps include copy, merge, resolve conflicts, and finish

"Behind the scenes" with an Explore:

1. Looker makes a copy of the LookML object being extended.
2. The copy, or extending object, is merged with the new or modified definitions.
3. If any conflicts are detected (which happens if you modified definitions), the extending object controls.
4. The extending object can be used in your LookML model just like any other object.

#### Extend an Explore to add joins from another Explore
Instead of copying/pasting the same joins across multiple Explores in a model file, you can create one base Explore that contains the most commonly used joins across your Explores. Then you can use extends to reuse that base Explore to define and customize other Explores defined in the model file.

A common business use case for this is creating one core Explore that can be used to create other Explores for specific user groups/teams within your organization.

## Best practices for writing LookML code

### Use descriptive field names
Using descriptive field names to define dimensions and measures helps both business users and developers find what they need, [#1 in the best practices](https://help.looker.com/hc/en-us/articles/360001766908-Best-Practice-Create-a-Positive-Experience-for-Looker-Users). Some examples of this include:

- Name measures by their aggregate function or with common terms: ```total_[FIELD]``` for sum, ```count_[FIELD]```, ```avg_[FIELD]```, etc.
- Name ratios descriptively: percent_orders_by_returning_customer is clearer than percent_returning.
- Name **yesno** fields clearly: order_is_returned or is_order_returned, instead of returned.
- Avoid using the words "date" or "time" in a dimension group. Looker already appends each timeframe to the end of the dimension name. For example, created_date would become created_date_date.

### Leverage additional parameters
Leveraging additional parameters can help organize and provide more context for the data exposed to business users. You should include [labels](https://docs.looker.com/reference/field-params/label-for-field) and [descriptions](https://docs.looker.com/reference/field-params/description) to help business users identify which fields and Explores to use for their workflows, [#1 and #4 in best practices](https://help.looker.com/hc/en-us/articles/360001766908-Best-Practice-Create-a-Positive-Experience-for-Looker-Users).

You should also use the [**group_label**](https://help.looker.com/hc/en-us/articles/360001766908-Best-Practice-Create-a-Positive-Experience-for-Looker-Users) parameter to group similar fields and Explores into logical categories for easier navigation, [#2 in best practices](https://help.looker.com/hc/en-us/articles/360001766908-Best-Practice-Create-a-Positive-Experience-for-Looker-Users).

Finally, you should use [**drill_fields**](https://docs.looker.com/reference/field-params/drill_fields) to curate the additional options that a business user sees when they click on the value of a table cell while exploring data.

### Create and surface the fewest number of fields and Explores possible
Creating and surfacing the fewest number of fields and Explores possible while still allowing business users to easily access the answers they need is a very beneficial best practice to implement, [#3 in best practices](https://help.looker.com/hc/en-us/articles/360001766908-Best-Practice-Create-a-Positive-Experience-for-Looker-Users). The optimal number of fields and Explores is different for every business, but having too many of each tends to confuse end users.

You can use the [**fields**](https://docs.looker.com/reference/explore-params/fields-for-explore) parameter to limit fields surfaced to the business user in an individual Explore and use the [**hidden**](https://docs.looker.com/reference/field-params/hidden) parameter to hide a field or Explore across the entire model.

### Write sustainable and modular LookML code
Writing sustainable and modular LookML code that can easily be [updated, maintained, and reused](https://help.looker.com/hc/en-us/articles/360001784587-Best-Practice-Writing-Sustainable-Maintainable-LookML) is key to maintaining functional projects.

Although the organization and quality of the underlying LookML code might not be immediately apparent, it can also affect the overall business user experience. Specifically, if you (as a LookML developer) can spend less time writing and maintaining your base code, you can more quickly modify or implement attributes and features that are requested by business users.

Here are a few ideas for writing sustainable and modular LookML code:

- Use [substitution operators](https://docs.looker.com/data-modeling/learning-lookml/sql-and-referring-to-lookml#substitution_operator_(%24)) throughout your code to minimize hard-coded references to your underlying database.
- Identify appropriate cases for SQL-derived versus native-derived tables.
    - Native derived tables promote code reusability by leveraging existing LookML objects in your model to define new structures or aggregations that do not yet exist in your underlying database.
    - SQL derived tables are used for more custom or complex aggregations that are not easily accomplished with native derived tables.

- Use [extends](https://docs.looker.com/data-modeling/learning-lookml/extends) or [refinements](https://docs.looker.com/data-modeling/learning-lookml/refinements) to expand on existing views and Explores.
    - You can extend a view or Explore to make a copy of the original object and apply modifications. 
    - You can also create a refinement to adapt an existing view or Explore without editing the LookML file that contains it.

### Optimize the performance of Explore queries
To optimize the performance of Explore queries for business users:

- Avoid joining extraneous views in an Explore.
- Declare a primary key in the view file, and define a join relationship using the relationship parameter to ensure that correct aggregates are produced.
- Define many_to_one joins between views from the most granular level to the highest level of detail.
- Persist derived tables for complex queries that take a long time to run or for queries that are used frequently by a large number of users or applications.

For more information about these topics, see [Looker Dos and Don'ts](https://help.looker.com/hc/en-us/articles/360001784747-Best-Practice-LookML-Dos-and-Don-ts).

#### More References
- [LookML quick reference](https://docs.looker.com/reference/lookml-quick-reference)
- [LookML terms and concepts](https://docs.looker.com/data-modeling/learning-lookml/lookml-terms-and-concepts)
- [Join the Looker Community](https://community.looker.com/)
- [Additional LookML basics](https://docs.looker.com/data-modeling/learning-lookml/advanced-lookml-concepts)

## Looker Standard Labs
- [Looker Data Explorer - Qwik Start](https://www.cloudskillsboost.google/catalog_lab/3509)
- [Filtering and Sorting Data in Looker](https://www.cloudskillsboost.google/catalog_lab/3557)
- [Merging Results from Different Explores in Looker](https://www.cloudskillsboost.google/catalog_lab/3640)
- [Creating a Looker Modeled Query and Working with Quick Start](https://www.cloudskillsboost.google/catalog_lab/4137)
- [Looker Functions and Operators](https://www.cloudskillsboost.google/catalog_lab/3635)
- [Exploring Data with Looker: Challenge Lab](https://www.cloudskillsboost.google/catalog_lab/3679)
- [Looker Developer - Qwik Start](https://www.cloudskillsboost.google/catalog_lab/3838)
- [Troubleshooting Data Models in Looker](https://www.cloudskillsboost.google/catalog_lab/4745)
- [Creating Measures and Dimensions Using LookML](https://www.cloudskillsboost.google/catalog_lab/3837)
- [Creating Derived Tables Using LookML](https://www.cloudskillsboost.google/catalog_lab/3836)
- [Filtering Explores with LookML](https://www.cloudskillsboost.google/catalog_lab/3839)
- [Caching and Datagroups with LookML](https://www.cloudskillsboost.google/catalog_lab/3840)
- [Modularizing LookML Code with Extends](https://www.cloudskillsboost.google/catalog_lab/4094)
- [Employing Best Practices for Improving the Usability of LookML Projects](https://www.cloudskillsboost.google/catalog_lab/4746)
- [Optimizing Performance of LookML queries](https://www.cloudskillsboost.google/catalog_lab/4170)
- [Manage Data Models in Looker: Challenge Lab](https://www.cloudskillsboost.google/catalog_lab/4747)
- [Creating Tile-based Dashboard Alerts in Looker](https://www.cloudskillsboost.google/catalog_lab/6619)
- [Sending and Scheduling Dashboards in Looker](https://www.cloudskillsboost.google/catalog_lab/6621)
- [Answering Complex Questions Using Native Derived Tables with LookML](https://www.cloudskillsboost.google/catalog_lab/4093)
- [Creating dynamic SQL derived tables with LookML and Liquid](https://www.cloudskillsboost.google/catalog_lab/4090)

## Looker Studio Labs
- [Explore and Create Reports with Looker Studio](https://www.cloudskillsboost.google/catalog_lab/1450)
- [How to Build a BI Dashboard Using Google Looker Studio and BigQuery](https://www.cloudskillsboost.google/catalog_lab/1738)
- [Looker Studio: Qwik Start](https://www.cloudskillsboost.google/catalog_lab/768)
- [Get Started with Looker: Challenge Lab](https://www.cloudskillsboost.google/catalog_lab/6266)
- [Get Started with Looker](https://www.cloudskillsboost.google/course_templates/647)


