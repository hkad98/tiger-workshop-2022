# Instructions for workshop

The instructions are not set in stone, so it is only up to you how much time you spend on each step.

## Building your data stack E2E

We will build a data stack E2E. There is only one condition that is obvious because of dogfooding, and that is that you need to use GoodData. The rest is up to you.

## Data source

As engineers creating Tiger/Panther, you might be interested in the usage of the product you build. When discussing product use, the first things that come to mind are probably Matomo and Splunk logs. You have been granted access to the Redshift database where these logs are stored. 

Feel free to explore the database that you were granted. Each one of you have their own schema where you can create view etc.

 **Please  <span style="color:red"> DO NOT </span> create views in public schema.**

Redshift structure explenation from Jiri:
* *your_abbrevation* schema
  
  * contains two views with logs Matomo and Splunk 
  
* *public* schema
  
  * *src_** - landing layer = current extract from source systems (Splunk, Matomo, Metadata, Salesforce)
  * *stg_**  - stage layer =  historicized source data
  * *d_** + *f_** dataware house layer = facts + dimensions
  * *wrk_** - wrk tabulky  = tables that are not final for transformation operations
  

## [Optional] Hands on dbt

> **Note**
> Suppose you choose to try out dbt. Be aware that the hands-on experience requires a lot of self-studying.


[dbt](https://docs.getdbt.com/docs/introduction) is popular transofrmation workflow with a strong community and [open source dbt Core](https://github.com/dbt-labs/dbt-core).

> **Warning**
> As you found out, dbt is a transformation workflow tool. So be careful during a transformation, so you do not delete or overwrite your data.

I recommend you to try out [dbt Core](https://docs.getdbt.com/docs/get-started/getting-started-dbt-core) but if you want there is nothing holding you back to try out [dbt Cloud](https://docs.getdbt.com/docs/get-started/getting-started/set-up-dbt-cloud) (registration needed).

### Instalation

For the installation of dbt Cloud follow the [documenation](https://docs.getdbt.com/docs/get-started/installation). You can choose from several methods.

### First steps

To get to know dbt more I strongly recommend you to read and follow [Getting started with dbt Core](https://docs.getdbt.com/docs/get-started/getting-started-dbt-core) chapter in documentation.

## Set up you environment using Python

I had a presentation on Tiger scholar presenting Python SDK and its usage. Can you remember what I showed you?
In this chapter, I encourage you to set up the following things using Python SDK:

* Create workspace 
* Create data source
* Scan and put PDM
* Generate and put LDM

Play around with:
* User groups
* Permission settings
* Workspace data filters (Note: no entity support on backend)

### Useful links:
* [gooddata-sdk PyPI](https://pypi.org/project/gooddata-sdk/)
* [gooddata-sdk documentation](https://gooddata-sdk.readthedocs.io/en/stable/)
  
Need help with Python? Contact me.

## Analytics model in UI

Let's play around. How many of the following questions can you answer using an insight or dashboard?

* How many internal/external users use Python SDK?
* Which API calls are the most used in the context of Python SDK?
* How many people created their data source in trial?
  * Which one was it? 
  * How many tables were in the model?
* Has anyone used workspace hierarchies in the trial?
  * How deep the hierarchy was?
  * Did they set up workspace data filters?



## [Optional] Can you make a pipeline?

Imagine that you are a company that sells analytics using GoodData. Your clients want to have working dashboards and insights; therefore, you have several environments to support your client's desires.

Let's have workspaces (aka environments):
* development
* stagging
* production

Can you set up a GitLab project using Python SDK and GitLab pipelines to deliver all features?

For the proper delivery, it would be great to set some tests. E.g., are all insights computable? 

## Data consumption

Can you consume data from GoodData with other tools? 

There are other visualization tools such as:

* [Apache Superset](https://superset.apache.org/)
* [Metabase](https://www.metabase.com/)
* [Redash](https://redash.io/)
* [Motor Admin](https://www.getmotoradmin.com/)

You can use their docker images and connect to them using [GoodData FDW](https://gooddata-fdw.readthedocs.io/en/latest/).

Are experienced with data science, machine learning or do you want to gain experience? Let's try to use [GoodPandas](https://gooddata-pandas.readthedocs.io/) and let's check some interesting Python science libraries such as:

* [scikit-learn](https://pypi.org/project/scikit-learn/) - machine learning
* [matplotlib](https://pypi.org/project/matplotlib/) - visualization
* [seaborn](https://pypi.org/project/seaborn/) - statistical data visualization

## Presentation + feedback

Let's share what you were able to manage. Did you find any valuable insights? Did you struggle with something? Did you find a bug?

Please prepare a presentation. You can have slides, or you can go step by step and show us what you achieved.