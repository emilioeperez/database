# Lab 4: Privately Connect Your Own Data Sources to Boost AI Insights

## Introduction

In this lab session, you will learn how to add your own enterprise data sources, including structured data sources, web sources and REST APIs, to Oracle Private AI Agent Studio.

**Estimated time:** 10 minutes.

### Objectives

By the end of this lab, you will be able to:

- Integrate and configure databases as  private data sources for your AI agents.
- Add and configure web sources to extend your agents' knowledge base.
- Securely connect REST APIs as custom data sources using OpenAPI specifications.
- Enrich agent knowledge by adding documentation as a file data source.
- Manage, edit, or remove connected data sources to maintain data privacy and control.

### Prerequisites

To follow this tutorial, it is suggested that you have access to an Oracle Private AI Agent Studio environment with permissions to add and manage data sources.

## Task 1: Add a structured data source

Structured data sources, such as relational databases, can be connected to provide comprehensive, organized information for your data analysis agents.

This feature enables the integration with enterprise databases like Oracle Database, allowing agents to run queries and analyze data. Only SELECT-like queries are supported for security and governance. Access is managed according to user credentials and roles, ensuring appropriate data governance and compliance.

1. Open Oracle Private AI Agent Studio and log in. In the sidebar, click the **Data Sources** section.

    ![Data Sources](images/left_panel.png)

    ![Data Sources](images/data_sources.png)

2. Click the **Add Data Source** button. A setup form will be displayed, allowing you to add Web Sources, Databases or REST APIs. For this task, select Database.

    ![Data Source Database](images/datasource_add_database.png)

3. After completing the form with necessary information, press the **Test Connection** button. If the connection is successful, a "Database connection successful" message will be displayed. Then, click the **Add Database Source** button. The newly added data source will appear in the list.

## Task 2: Add a Web Source data source

Web data sources allow you to use publicly available website content, including unauthenticated web pages, as a knowledge base for your agents.

This feature lets you configure how often a site is crawled for new or updated information, whether to use a proxy, and set the depth of link exploration. By adding a Web Source, you can easily expand the accessible information for your agents and ensure the knowledge base remains current and accurate as the system regularly checks for updates.

![Web Source Data Source](images/datasource_add_websource.png)

To add a web source, follow a process similar to adding a database.

1. In the Data Sources section, click the Add **Data Source button**, select Web Source.

2. Complete the form by entering a Source Name, Description, Endpoint, and any file extensions exclude, such as .pdf and .doc.

3. Set up URL filters to include or exclude specific URL patterns from the crawl. You can also configure the crawl depth (the maximum number of links to follow from the start endpoint), select an unlimited crawl option, specify the refresh frequency in days, and optionally enter a proxy URL.

4. Once the form is filled click **Add Web Source**.

Depending on your configuration the ingestion of the web data source may take a from seconds up to  minutes.

## Task 3: Add a REST API data source

Oracle Private AI Agent Studio allows you to add a REST API as data sources. OpenAPI-compatible REST APIs are web services described in a standardized format, enabling easy integration and automated interaction with agent platforms.

Following this industry standard ensures clearly defined API endpoints, HTTP methods, input/output parameters, authentication methods, and expected responses. APIs described in the OpenAPI format are easily discovered, consumed, and integrated across platforms and tools.

![REST API Data Source](images/datasource_add_rest_api.png)

You can add a OpenAPI-compatible REST API by simply dragging and dropping your OpenAPI 2.0+ specification JSON file; the API endpoints will be automatically configured.

Optionally, click **Advanced Configuration** to add a source name and description.

Click **Add REST API Source** to include it among your collection of secure and custom enterprise data sources.

## Task 4: Add a File data source

Oracle Private AI Agent Studio allows you to add files as data sources. Adding your own PDF files enables your agents to access to more robust and up-to-date knowledge base, removing the need to convert your documentation to other formats.

![File Data Source](images/datasource_add_file.png)

Add a file as a data source by assigning a name and description, then simply dragging and dropping the file into the designated box. Click **Add File Source** to enrich your knowledge base with your documents.

## Task 5: Manage your custom data sources

![Data source collection](images/datasource_collection.png)

Oracle Private AI Agent Studio allows you to edit or delete previously added data sources at any time, allowing you to effectively manage the information accessible to your agents.

## Summary

This concludes the current module. You are now able to add your own data sources to enhance your custom agents and workflows in an air-gapped, private environment. The next modules will explore each feature of Oracle Private AI Agent Studio in greater detail. Continue with them so you don't miss on new discoveries and learning opportunities. You may now **proceed to the next lab**.

## Acknowledgements

- **Author** - Emilio Perez, Member of Technical Staff, Database Applied AI
- **Last Updated By/Date** - Emilio Perez - August 2025
