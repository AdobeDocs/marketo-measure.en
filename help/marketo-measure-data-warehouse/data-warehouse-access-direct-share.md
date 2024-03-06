---
description: Data Warehouse Access - Direct Share - Product Documentation
title: Data Warehouse Access - Direct Share
exl-id: 940c3316-5f94-4aa2-a656-aec5eb7b7450
feature: Data Warehouse
---
# Data Warehouse Access - Direct Share {#data-warehouse-access-direct-share}

## Requirements {#requirements}

For [!DNL Marketo Measure] to set up a direct share to the data warehouse you must meet the following requirements.

* You have your own Snowflake instance.
* Your Snowflake instance is in the Azure East US 2 Snowflake region.
* You provide [!DNL Marketo Measure] with your Snowflake account id.

## Limitations {#limitations}

[!DNL Marketo Measure] will only be able to set up Snowflake Direct Shares with accounts located in Azure East US 2 due to current Snowflake Direct Share limitations. If you require your data to be made available in other Snowflake regions, we recommend making a copy of the data in a Snowflake account located in Azure East US 2 and using the [Snowflake Database Replication](https://docs.snowflake.com/en/user-guide/database-replication-intro.html){target="_blank"} feature to copy your data in the Snowflake region/account of your choice.

## Enter Snowflake Account ID {#enter-snowflake-account-id}

Open the **Settings** section in the Marketo Measure app and navigate to the **Data Warehouse** page. In the **Direct Share** section, enter your [Snowflake account id](https://docs.snowflake.com/en/user-guide/admin-account-identifier.html){target="_blank"} in the box provided and click **Connect**.

![](assets/data-warehouse-access-direct-share-1.png)

## Accessing the Share {#accessing-the-share}

After the share is created for the account ID provided, you must complete the [setup steps](https://docs.snowflake.com/en/user-guide/data-share-consumers.html){target="_blank"} within your Snowflake instance to access the data.

>[!NOTE]
>
>You can choose any database name you want. You can assign the privileges to any role you choose, so long as it exists in your Snowflake instance.

* Use the Account Admin role

```
USE ROLE ACCOUNTADMIN
```

* View available shares (this shows the name of the share granted)

```
SHOW SHARES
```

* Create a database for the share

```
CREATE DATABASE <database_name> FROM SHARE <provider_account>.<share_name>
```

* Grant privileges on the shared database

```
GRANT IMPORTED PRIVILEGES ON DATABASE <database_name> TO ROLE <role_name>
GRANT IMPORTED PRIVILEGES ON ALL SCHEMAS IN DATABASE <database_name> TO ROLE <role_name>
```

For more detailed instructions and steps to accomplish these steps from the Snowflake UI, reference [Snowflake's documentation directly](https://docs.snowflake.com/en/user-guide/data-share-consumers.html){target="_blank"}.
