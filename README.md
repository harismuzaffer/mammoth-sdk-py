# mammoth-analytics

Developer-friendly & type-safe Python SDK specifically catered to leverage *mammoth-analytics* API.

<div align="left">
    <a href="https://www.speakeasy.com/?utm_source=mammoth-analytics&utm_campaign=python"><img src="https://www.speakeasy.com/assets/badges/built-by-speakeasy.svg" /></a>
    <a href="https://opensource.org/licenses/MIT">
        <img src="https://img.shields.io/badge/License-MIT-blue.svg" style="width: 100px; height: 28px;" />
    </a>
</div>


<br /><br />
> [!IMPORTANT]
> This SDK is not yet ready for production use. To complete setup please follow the steps outlined in your [workspace](https://app.speakeasy.com/org/mammoth-analytics/litestar). Delete this section before > publishing to a package manager.

<!-- Start Summary [summary] -->
## Summary

Mammoth Analytics: 
Mammoth API : helps you do use mammoth app functionalities via API.
<!-- End Summary [summary] -->

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
* [mammoth-analytics](#mammoth-analytics)
  * [SDK Installation](#sdk-installation)
  * [IDE Support](#ide-support)
  * [SDK Example Usage](#sdk-example-usage)
  * [Authentication](#authentication)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [File uploads](#file-uploads)
  * [Retries](#retries)
  * [Error Handling](#error-handling)
  * [Custom HTTP Client](#custom-http-client)
  * [Resource Management](#resource-management)
  * [Debugging](#debugging)
* [Development](#development)
  * [Maturity](#maturity)
  * [Contributions](#contributions)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

> [!TIP]
> To finish publishing your SDK to PyPI you must [run your first generation action](https://www.speakeasy.com/docs/github-setup#step-by-step-guide).


> [!NOTE]
> **Python version upgrade policy**
>
> Once a Python version reaches its [official end of life date](https://devguide.python.org/versions/), a 3-month grace period is provided for users to upgrade. Following this grace period, the minimum python version supported in the SDK will be updated.

The SDK can be installed with *uv*, *pip*, or *poetry* package managers.

### uv

*uv* is a fast Python package installer and resolver, designed as a drop-in replacement for pip and pip-tools. It's recommended for its speed and modern Python tooling capabilities.

```bash
uv add git+<UNSET>.git
```

### PIP

*PIP* is the default package installer for Python, enabling easy installation and management of packages from PyPI via the command line.

```bash
pip install git+<UNSET>.git
```

### Poetry

*Poetry* is a modern tool that simplifies dependency management and package publishing by using a single `pyproject.toml` file to handle project metadata and dependencies.

```bash
poetry add git+<UNSET>.git
```

### Shell and script usage with `uv`

You can use this SDK in a Python shell with [uv](https://docs.astral.sh/uv/) and the `uvx` command that comes with it like so:

```shell
uvx --from mammoth-analytics python
```

It's also possible to write a standalone Python script without needing to set up a whole project like so:

```python
#!/usr/bin/env -S uv run --script
# /// script
# requires-python = ">=3.9"
# dependencies = [
#     "mammoth-analytics",
# ]
# ///

from mammoth_analytics import MammothAnalytics

sdk = MammothAnalytics(
  # SDK arguments
)

# Rest of script here...
```

Once that is saved to a file, you can run it with `uv run script.py` where
`script.py` can be replaced with the actual file name.
<!-- End SDK Installation [installation] -->

<!-- Start IDE Support [idesupport] -->
## IDE Support

### PyCharm

Generally, the SDK will work well with most IDEs out of the box. However, when using PyCharm, you can enjoy much better integration with Pydantic by installing an additional plugin.

- [PyCharm Pydantic Plugin](https://docs.pydantic.dev/latest/integrations/pycharm/)
<!-- End IDE Support [idesupport] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

```python
# Synchronous Example
from mammoth_analytics import MammothAnalytics, models
import os


with MammothAnalytics(
    server_url="https://api.example.com",
    security=models.Security(
        api_key=os.getenv("MAMMOTHANALYTICS_API_KEY", ""),
        api_secret=os.getenv("MAMMOTHANALYTICS_API_SECRET", ""),
    ),
) as ma_client:

    ma_client.projects.add_user(workspace_id=4, project_id=4, users=[
        {
            "user_id": 4,
            "role_name": models.RoleName.PROJECT_ADMIN,
        },
    ])

    # Use the SDK ...
```

</br>

The same SDK client can also be used to make asynchronous requests by importing asyncio.
```python
# Asynchronous Example
import asyncio
from mammoth_analytics import MammothAnalytics, models
import os

async def main():

    async with MammothAnalytics(
        server_url="https://api.example.com",
        security=models.Security(
            api_key=os.getenv("MAMMOTHANALYTICS_API_KEY", ""),
            api_secret=os.getenv("MAMMOTHANALYTICS_API_SECRET", ""),
        ),
    ) as ma_client:

        await ma_client.projects.add_user_async(workspace_id=4, project_id=4, users=[
            {
                "user_id": 4,
                "role_name": models.RoleName.PROJECT_ADMIN,
            },
        ])

        # Use the SDK ...

asyncio.run(main())
```
<!-- End SDK Example Usage [usage] -->

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security schemes globally:

| Name         | Type   | Scheme  | Environment Variable          |
| ------------ | ------ | ------- | ----------------------------- |
| `api_key`    | apiKey | API key | `MAMMOTHANALYTICS_API_KEY`    |
| `api_secret` | apiKey | API key | `MAMMOTHANALYTICS_API_SECRET` |

You can set the security parameters through the `security` optional parameter when initializing the SDK client instance. The selected scheme will be used by default to authenticate with the API for all operations that support it. For example:
```python
from mammoth_analytics import MammothAnalytics, models
import os


with MammothAnalytics(
    server_url="https://api.example.com",
    security=models.Security(
        api_key=os.getenv("MAMMOTHANALYTICS_API_KEY", ""),
        api_secret=os.getenv("MAMMOTHANALYTICS_API_SECRET", ""),
    ),
) as ma_client:

    ma_client.projects.add_user(workspace_id=4, project_id=4, users=[
        {
            "user_id": 4,
            "role_name": models.RoleName.PROJECT_ADMIN,
        },
    ])

    # Use the SDK ...

```
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [accept_invite](docs/sdks/acceptinvite/README.md)

* [accept](docs/sdks/acceptinvite/README.md#accept) - Accept invitation to workspace

### [app_usage](docs/sdks/appusage/README.md)

* [get](docs/sdks/appusage/README.md#get) - Get app usage details

### [automations](docs/sdks/automations/README.md)

* [list](docs/sdks/automations/README.md#list) - Get list of automations
* [create](docs/sdks/automations/README.md#create) - Create automation
* [get](docs/sdks/automations/README.md#get) - Get automation data
* [delete](docs/sdks/automations/README.md#delete) - Delete automation and its tasks
* [update](docs/sdks/automations/README.md#update) - Update automation related data

### [batches](docs/sdks/batches/README.md)

* [list](docs/sdks/batches/README.md#list) - List batches
* [create](docs/sdks/batches/README.md#create) - Create batch
* [remove](docs/sdks/batches/README.md#remove) - Delete multiple batches
* [update](docs/sdks/batches/README.md#update) - Update batches
* [get](docs/sdks/batches/README.md#get) - List batches
* [delete](docs/sdks/batches/README.md#delete) - Delete batch

### [browse](docs/sdks/browse/README.md)

* [get](docs/sdks/browse/README.md#get) - Browse and discover resources
* [folders](docs/sdks/browse/README.md#folders) - Browse and discover folder resources
* [get_project](docs/sdks/browse/README.md#get_project) - Browse and discover project resources
* [workspace](docs/sdks/browse/README.md#workspace) - Browse and discover workspace resources

### [chargebee_plan](docs/sdks/chargebeeplan/README.md)

* [get](docs/sdks/chargebeeplan/README.md#get) - Get Chargebee plan

### [client_apps](docs/sdks/clientapps/README.md)

* [get_details](docs/sdks/clientapps/README.md#get_details) - Get client app details
* [delete](docs/sdks/clientapps/README.md#delete) - Delete a client app
* [update](docs/sdks/clientapps/README.md#update) - Update client app
* [list](docs/sdks/clientapps/README.md#list) - Get list of client apps
* [create](docs/sdks/clientapps/README.md#create) - Create api tokens to access api

### [conditional_format](docs/sdks/conditionalformat/README.md)

* [get](docs/sdks/conditionalformat/README.md#get) - get conditional format
* [delete](docs/sdks/conditionalformat/README.md#delete) - delete conditional format
* [update](docs/sdks/conditionalformat/README.md#update) - update conditional format

### [conditional_formats](docs/sdks/conditionalformats/README.md)

* [create](docs/sdks/conditionalformats/README.md#create) - create conditional format

### [connections](docs/sdks/connections/README.md)

* [get](docs/sdks/connections/README.md#get) - Get Connection
* [delete](docs/sdks/connections/README.md#delete) - Delete Connection
* [update](docs/sdks/connections/README.md#update) - Update Connection
* [list](docs/sdks/connections/README.md#list) - List Connections
* [create](docs/sdks/connections/README.md#create) - Create Connection

### [connector_profiles](docs/sdks/connectorprofiles/README.md)

* [add_connector](docs/sdks/connectorprofiles/README.md#add_connector) - Add connector to profile
* [list](docs/sdks/connectorprofiles/README.md#list) - List all connector profiles
* [create](docs/sdks/connectorprofiles/README.md#create) - Create a new connector profile
* [update](docs/sdks/connectorprofiles/README.md#update) - Update a connector profile
* [delete](docs/sdks/connectorprofiles/README.md#delete) - Delete a connector profile

### [connectors](docs/sdks/connectors/README.md)

* [fetch](docs/sdks/connectors/README.md#fetch) - List all connectors
* [create](docs/sdks/connectors/README.md#create) - Create a new connector
* [update](docs/sdks/connectors/README.md#update) - Update a connector
* [delete](docs/sdks/connectors/README.md#delete) - Delete a connector
* [get](docs/sdks/connectors/README.md#get) - Get connector details
* [list](docs/sdks/connectors/README.md#list) - List connectors

### [datasets](docs/sdks/datasets/README.md)

* [list](docs/sdks/datasets/README.md#list) - Get list of datasets
* [create](docs/sdks/datasets/README.md#create) - Create dataset
* [remove](docs/sdks/datasets/README.md#remove) - Delete multiple datasets
* [rename](docs/sdks/datasets/README.md#rename) - Update datasets name
* [get](docs/sdks/datasets/README.md#get) - Get dataset details
* [delete](docs/sdks/datasets/README.md#delete) - Delete dataset
* [update](docs/sdks/datasets/README.md#update) - Update dataset
* [get_data](docs/sdks/datasets/README.md#get_data) - Get dataset data

### [dataview_pipeline](docs/sdks/dataviewpipeline/README.md)

* [get](docs/sdks/dataviewpipeline/README.md#get) - Get dataview pipeline information
* [edit](docs/sdks/dataviewpipeline/README.md#edit) - Edit and perform bulk operations on a dataview pipeline

### [dataview_pipeline_export](docs/sdks/dataviewpipelineexport/README.md)

* [delete](docs/sdks/dataviewpipelineexport/README.md#delete) - Delete an export

### [dataview_pipeline_exports](docs/sdks/dataviewpipelineexports/README.md)

* [list](docs/sdks/dataviewpipelineexports/README.md#list) - Get dataview pipeline exports information
* [add](docs/sdks/dataviewpipelineexports/README.md#add) - Add a export in the pipeline
* [get](docs/sdks/dataviewpipelineexports/README.md#get) - Get dataview pipeline export information
* [edit](docs/sdks/dataviewpipelineexports/README.md#edit) - Edit a dataview pipeline export

### [dataview_pipeline_tasks](docs/sdks/dataviewpipelinetasks/README.md)

* [get_pipeline_tasks](docs/sdks/dataviewpipelinetasks/README.md#get_pipeline_tasks) - Get dataview pipeline tasks information
* [add](docs/sdks/dataviewpipelinetasks/README.md#add) - Add a task in the pipeline
* [get](docs/sdks/dataviewpipelinetasks/README.md#get) - Get dataview pipeline task information
* [delete](docs/sdks/dataviewpipelinetasks/README.md#delete) - Delete a task
* [edit](docs/sdks/dataviewpipelinetasks/README.md#edit) - Edit a dataview pipeline task

### [dataviews](docs/sdks/dataviews/README.md)

* [list](docs/sdks/dataviews/README.md#list) - Get list of dataviews present in a dataset
* [add](docs/sdks/dataviews/README.md#add) - Create or duplicate dataview
* [delete_multiple](docs/sdks/dataviews/README.md#delete_multiple) - Delete multiple dataviews
* [get_information](docs/sdks/dataviews/README.md#get_information) - Get dataview information
* [delete](docs/sdks/dataviews/README.md#delete) - Delete dataview safely
* [patch](docs/sdks/dataviews/README.md#patch) - Patch dataview
* [get_active_users](docs/sdks/dataviews/README.md#get_active_users) - Get list of active users on this dataview
* [mark_active_user](docs/sdks/dataviews/README.md#mark_active_user) - Mark active user on this dataview
* [get_data](docs/sdks/dataviews/README.md#get_data) - Get dataview data
* [retrievedata](docs/sdks/dataviews/README.md#retrievedata) - Get dataview data
* [ai_suggestions](docs/sdks/dataviews/README.md#ai_suggestions) - Generate AI-based Suggestions for Dataview
* [generate_sql](docs/sdks/dataviews/README.md#generate_sql) - Generate SQL query based on intent
* [generate_profile](docs/sdks/dataviews/README.md#generate_profile) - Generate or Update Dataset Profile

### [deauthorization](docs/sdks/deauthorization/README.md)

* [delete_user_data](docs/sdks/deauthorization/README.md#delete_user_data) - Delete user's data from the system

### [ds_config](docs/sdks/dsconfigsdk/README.md)

* [get](docs/sdks/dsconfigsdk/README.md#get) - Get ds config details
* [delete](docs/sdks/dsconfigsdk/README.md#delete) - Delete ds configs

### [ds_configs](docs/sdks/dsconfigs/README.md)

* [remove](docs/sdks/dsconfigs/README.md#remove) - Delete ds config
* [update](docs/sdks/dsconfigs/README.md#update) - Validate and get sample data
* [list](docs/sdks/dsconfigs/README.md#list) - List ds configs
* [validate_and_fetch_data](docs/sdks/dsconfigs/README.md#validate_and_fetch_data) - Validate and get sample data

### [external_key](docs/sdks/externalkeysdk/README.md)

* [get](docs/sdks/externalkeysdk/README.md#get) - Get the given external key

### [external_keys](docs/sdks/externalkeys/README.md)

* [get_by_workspace_id](docs/sdks/externalkeys/README.md#get_by_workspace_id) - Get external keys of the given Workspace ID
* [add](docs/sdks/externalkeys/README.md#add) - Add external keys to access the intended services
* [delete](docs/sdks/externalkeys/README.md#delete) - Delete an external key

### [feature_profiles](docs/sdks/featureprofiles/README.md)

* [add_feature](docs/sdks/featureprofiles/README.md#add_feature) - Add feature to profile
* [list](docs/sdks/featureprofiles/README.md#list) - List all feature profiles
* [create](docs/sdks/featureprofiles/README.md#create) - Create a new feature profile
* [update](docs/sdks/featureprofiles/README.md#update) - Update a feature profile
* [delete](docs/sdks/featureprofiles/README.md#delete) - Delete a feature profile

### [features](docs/sdks/features/README.md)

* [list](docs/sdks/features/README.md#list) - List all features
* [create](docs/sdks/features/README.md#create) - Create a new feature
* [update](docs/sdks/features/README.md#update) - Update a feature
* [delete](docs/sdks/features/README.md#delete) - Delete a feature

### [files](docs/sdks/files/README.md)

* [list](docs/sdks/files/README.md#list) - List files
* [create_dataset](docs/sdks/files/README.md#create_dataset) - Upload file or folder
* [remove](docs/sdks/files/README.md#remove) - Delete files
* [get](docs/sdks/files/README.md#get) - Get file details
* [delete](docs/sdks/files/README.md#delete) - Delete file
* [update_configs](docs/sdks/files/README.md#update_configs) - Updates the file configs

### [folders](docs/sdks/folders/README.md)

* [list](docs/sdks/folders/README.md#list) - List folders
* [create](docs/sdks/folders/README.md#create) - Create Folder
* [remove](docs/sdks/folders/README.md#remove) - Delete folders
* [update_resources](docs/sdks/folders/README.md#update_resources) - Move resources from/to folder
* [get](docs/sdks/folders/README.md#get) - Get Folder Details
* [delete](docs/sdks/folders/README.md#delete) - Delete Folder
* [update](docs/sdks/folders/README.md#update) - Updates the folder details

### [generate_ai_based_data](docs/sdks/generateaibaseddata/README.md)

* [get_validation_info](docs/sdks/generateaibaseddata/README.md#get_validation_info) - Get validation information

### [generate_ai_data](docs/sdks/generateaidata/README.md)

* [preview](docs/sdks/generateaidata/README.md#preview) - Generate AI preview data for a dataview for the given sequence

### [generate_data_based_on_ai](docs/sdks/generatedatabasedonai/README.md)

* [ai_suggestions](docs/sdks/generatedatabasedonai/README.md#ai_suggestions) - Generate AI-based Suggestions for Dataview

### [generate_profile](docs/sdks/generateprofile/README.md)

* [generate_profile](docs/sdks/generateprofile/README.md#generate_profile) - Generate or Update Dataset Profile

### [jobs](docs/sdks/jobs/README.md)

* [get](docs/sdks/jobs/README.md#get) - Get job by id
* [list](docs/sdks/jobs/README.md#list) - Track multiple job ids


### [owner_user_control_settings](docs/sdks/ownerusercontrolsettings/README.md)

* [list_users](docs/sdks/ownerusercontrolsettings/README.md#list_users) - List users of all workspaces
* [transfer_ownerships](docs/sdks/ownerusercontrolsettings/README.md#transfer_ownerships) - Transfer ownerships of the workspaces

### [pipeline_items](docs/sdks/pipelineitems/README.md)

* [get](docs/sdks/pipelineitems/README.md#get) - Get dataview pipeline items

### [preferences](docs/sdks/preferences/README.md)

* [get](docs/sdks/preferences/README.md#get) - Fetch user preferences
* [update](docs/sdks/preferences/README.md#update) - Update user preferences

### [projects](docs/sdks/projects/README.md)

* [add_user](docs/sdks/projects/README.md#add_user) - Add user to a project
* [remove_user](docs/sdks/projects/README.md#remove_user) - Remove user from a project
* [update_user](docs/sdks/projects/README.md#update_user) - Update user role on a project
* [list](docs/sdks/projects/README.md#list) - Get list of projects
* [create](docs/sdks/projects/README.md#create) - Create a new project in given workspace
* [remove_all](docs/sdks/projects/README.md#remove_all) - Delete multiple projects
* [update](docs/sdks/projects/README.md#update) - Update multiple projects by adding/removing users or changing roles of the users
* [delete](docs/sdks/projects/README.md#delete) - Delete a project
* [rename](docs/sdks/projects/README.md#rename) - Update a project
* [get_pending_changes](docs/sdks/projects/README.md#get_pending_changes) - Get pending changes for a project
* [get_resource_status](docs/sdks/projects/README.md#get_resource_status) - Get resource status

### [query_gen](docs/sdks/querygen/README.md)

* [get_chat_status](docs/sdks/querygen/README.md#get_chat_status) - Get status
* [get_suggestion](docs/sdks/querygen/README.md#get_suggestion) - Generate query

### [registration_support](docs/sdks/registrationsupport/README.md)

* [register](docs/sdks/registrationsupport/README.md#register) - Register a user
* [update_user_verification](docs/sdks/registrationsupport/README.md#update_user_verification) - Update user details

### [reports](docs/sdks/reports/README.md)

* [list](docs/sdks/reports/README.md#list) - Get list of reports

### [schedules](docs/sdks/schedules/README.md)

* [list](docs/sdks/schedules/README.md#list) - Get list of schedules
* [create](docs/sdks/schedules/README.md#create) - Create schedule
* [get](docs/sdks/schedules/README.md#get) - Get schedule data
* [delete](docs/sdks/schedules/README.md#delete) - Delete schedule data
* [patch](docs/sdks/schedules/README.md#patch) - Patch schedule related data

### [self_](docs/sdks/self/README.md)

* [upload_profile_pic](docs/sdks/self/README.md#upload_profile_pic) - Add profile picture
* [delete_avatar](docs/sdks/self/README.md#delete_avatar) - Delete profile picture
* [delete](docs/sdks/self/README.md#delete) - Delete self
* [update_user](docs/sdks/self/README.md#update_user) - Update user details

### [self_serve_subscription_plans](docs/sdks/selfservesubscriptionplans/README.md)

* [list](docs/sdks/selfservesubscriptionplans/README.md#list) - List all subscription plans for self-serve

### [shopify_privacy_webhooks](docs/sdks/shopifyprivacywebhooks/README.md)

* [redact_customer](docs/sdks/shopifyprivacywebhooks/README.md#redact_customer) - Delete requested shopify customer orders data from the system
* [data_request](docs/sdks/shopifyprivacywebhooks/README.md#data_request) - Get requested data of shopify user
* [shop_redact](docs/sdks/shopifyprivacywebhooks/README.md#shop_redact) - Delete requested shopify shop's data from the system

### [split_segments](docs/sdks/splitsegments/README.md)

* [get](docs/sdks/splitsegments/README.md#get) - Get segments and features
* [update](docs/sdks/splitsegments/README.md#update) - Update segments with workspace Id

### [sql_generation](docs/sdks/sqlgeneration/README.md)

* [generate_sql](docs/sdks/sqlgeneration/README.md#generate_sql) - Generate SQL query based on intent

### [stripe_subscriptions](docs/sdks/stripesubscriptions/README.md)

* [cancel_workspace](docs/sdks/stripesubscriptions/README.md#cancel_workspace) - Cancel workspace subscription in Stripe
* [create_checkout_url](docs/sdks/stripesubscriptions/README.md#create_checkout_url) - Create Stripe checkout URL for workspace subscription
* [create_portal_url](docs/sdks/stripesubscriptions/README.md#create_portal_url) - Create Stripe customer portal URL
* [get](docs/sdks/stripesubscriptions/README.md#get) - Get workspace subscription from Stripe
* [create_workspace](docs/sdks/stripesubscriptions/README.md#create_workspace) - Create Stripe subscription for workspace
* [get_payment_methods](docs/sdks/stripesubscriptions/README.md#get_payment_methods) - Get workspace payment methods from Stripe
* [get_upcoming_invoice](docs/sdks/stripesubscriptions/README.md#get_upcoming_invoice) - Get upcoming invoice from Stripe
* [get_billing_history](docs/sdks/stripesubscriptions/README.md#get_billing_history) - Get workspace billing history from Stripe
* [get_workspace_status](docs/sdks/stripesubscriptions/README.md#get_workspace_status) - Get workspace subscription status
* [get_usage](docs/sdks/stripesubscriptions/README.md#get_usage) - Get workspace usage from Stripe

### [stripe_webhooks](docs/sdks/stripewebhooks/README.md)

* [handle](docs/sdks/stripewebhooks/README.md#handle) - Handle Stripe webhook

### [subscription](docs/sdks/subscriptionsdk/README.md)

* [fetch_hosted_page](docs/sdks/subscriptionsdk/README.md#fetch_hosted_page) - Get hosted pages
* [get_invoice](docs/sdks/subscriptionsdk/README.md#get_invoice) - Get associated plan details
* [update_detail](docs/sdks/subscriptionsdk/README.md#update_detail) - Update subscription details

### [subscription_access_control](docs/sdks/subscriptionaccesscontrol/README.md)

* [check_connector](docs/sdks/subscriptionaccesscontrol/README.md#check_connector) - Check connector access for workspace
* [check_feature_access](docs/sdks/subscriptionaccesscontrol/README.md#check_feature_access) - Check feature access for workspace
* [check_usage_limits](docs/sdks/subscriptionaccesscontrol/README.md#check_usage_limits) - Check usage limits for workspace

### [subscription_plans](docs/sdks/subscriptionplans/README.md)

* [archive](docs/sdks/subscriptionplans/README.md#archive) - Archive a subscription plan
* [list](docs/sdks/subscriptionplans/README.md#list) - List all subscription plans
* [create](docs/sdks/subscriptionplans/README.md#create) - Create a new subscription plan
* [get](docs/sdks/subscriptionplans/README.md#get) - Get a specific plan
* [update](docs/sdks/subscriptionplans/README.md#update) - Update a subscription plan
* [delete](docs/sdks/subscriptionplans/README.md#delete) - Delete a subscription plan
* [update_storage_tiers](docs/sdks/subscriptionplans/README.md#update_storage_tiers) - Update storage tiers for a plan

### [subscriptions](docs/sdks/subscriptions/README.md)

* [get_detail](docs/sdks/subscriptions/README.md#get_detail) - Get subscription details
* [list_invoices](docs/sdks/subscriptions/README.md#list_invoices) - List all invoices

### [subscriptions_support](docs/sdks/subscriptionssupport/README.md)

* [get_detail](docs/sdks/subscriptionssupport/README.md#get_detail) - Get subscription details
* [register](docs/sdks/subscriptionssupport/README.md#register) - Create subscription for workspace
* [update_subscription](docs/sdks/subscriptionssupport/README.md#update_subscription) - Update subscription for workspace
* [get_plans](docs/sdks/subscriptionssupport/README.md#get_plans) - Get available plans and other chargebee resources

### [users](docs/sdks/users/README.md)

* [get_self](docs/sdks/users/README.md#get_self) - Get request user details

### [users_support](docs/sdks/userssupport/README.md)

* [list](docs/sdks/userssupport/README.md#list) - Get users list
* [add_to_workspace](docs/sdks/userssupport/README.md#add_to_workspace) - Add a user to the workspace
* [transfer_roles](docs/sdks/userssupport/README.md#transfer_roles) - Transfer workspace ownership
* [remove](docs/sdks/userssupport/README.md#remove) - Remove a user in a workspace

### [webhooks](docs/sdks/webhooks/README.md)

* [list](docs/sdks/webhooks/README.md#list) - List webhooks
* [create](docs/sdks/webhooks/README.md#create) - Create a webhook
* [get_details](docs/sdks/webhooks/README.md#get_details) - Get webhook details
* [delete](docs/sdks/webhooks/README.md#delete) - Delete webhook
* [update](docs/sdks/webhooks/README.md#update) - Updates the webhook
* [add_data_using_get](docs/sdks/webhooks/README.md#add_data_using_get) - Add data to the webhook
* [add_data](docs/sdks/webhooks/README.md#add_data) - Add data to webhook

### [workspaces](docs/sdks/workspacessdk/README.md)

* [add_connector_addon](docs/sdks/workspacessdk/README.md#add_connector_addon) - Add connector addon to workspace
* [add_storage_addon](docs/sdks/workspacessdk/README.md#add_storage_addon) - Add storage addon to workspace
* [list_users](docs/sdks/workspacessdk/README.md#list_users) - Get users in workspace
* [add_user](docs/sdks/workspacessdk/README.md#add_user) - Add user in workspace
* [remove_member](docs/sdks/workspacessdk/README.md#remove_member) - Remove users or invites from workspace
* [modify_member](docs/sdks/workspacessdk/README.md#modify_member) - Resend invite, remove invitation, or change role in workspace
* [add_user_seats_addon](docs/sdks/workspacessdk/README.md#add_user_seats_addon) - Add user seats addon to workspace
* [list](docs/sdks/workspacessdk/README.md#list) - Get workspaces
* [create](docs/sdks/workspacessdk/README.md#create) - Create workspace
* [get](docs/sdks/workspacessdk/README.md#get) - Get workspace details
* [delete](docs/sdks/workspacessdk/README.md#delete) - Delete a workspace
* [update](docs/sdks/workspacessdk/README.md#update) - Update workspace
* [remove_user](docs/sdks/workspacessdk/README.md#remove_user) - Remove user from workspace/Leave workspace
* [update_user](docs/sdks/workspacessdk/README.md#update_user) - Change user role in workspace

### [workspaces_support](docs/sdks/workspacessupport/README.md)

* [list](docs/sdks/workspacessupport/README.md#list) - Get workspaces list
* [create](docs/sdks/workspacessupport/README.md#create) - Create new workspace
* [get_detail](docs/sdks/workspacessupport/README.md#get_detail) - Get workspace details
* [delete](docs/sdks/workspacessupport/README.md#delete) - Delete a workspace
* [update_detail](docs/sdks/workspacessupport/README.md#update_detail) - Update workspace details

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start File uploads [file-upload] -->
## File uploads

Certain SDK methods accept file objects as part of a request body or multi-part request. It is possible and typically recommended to upload files as a stream rather than reading the entire contents into memory. This avoids excessive memory consumption and potentially crashing with out-of-memory errors when working with very large files. The following example demonstrates how to attach a file stream to a request.

> [!TIP]
>
> For endpoints that handle file uploads bytes arrays can also be used. However, using streams is recommended for large files.
>

```python
from mammoth_analytics import MammothAnalytics, models
import os


with MammothAnalytics(
    server_url="https://api.example.com",
    security=models.Security(
        api_key=os.getenv("MAMMOTHANALYTICS_API_KEY", ""),
        api_secret=os.getenv("MAMMOTHANALYTICS_API_SECRET", ""),
    ),
) as ma_client:

    ma_client.self_.upload_profile_pic()

    # Use the SDK ...

```
<!-- End File uploads [file-upload] -->

<!-- Start Retries [retries] -->
## Retries

Some of the endpoints in this SDK support retries. If you use the SDK without any configuration, it will fall back to the default retry strategy provided by the API. However, the default retry strategy can be overridden on a per-operation basis, or across the entire SDK.

To change the default retry strategy for a single API call, simply provide a `RetryConfig` object to the call:
```python
from mammoth_analytics import MammothAnalytics, models
from mammoth_analytics.utils import BackoffStrategy, RetryConfig
import os


with MammothAnalytics(
    server_url="https://api.example.com",
    security=models.Security(
        api_key=os.getenv("MAMMOTHANALYTICS_API_KEY", ""),
        api_secret=os.getenv("MAMMOTHANALYTICS_API_SECRET", ""),
    ),
) as ma_client:

    ma_client.projects.add_user(workspace_id=4, project_id=4, users=[
        {
            "user_id": 4,
            "role_name": models.RoleName.PROJECT_ADMIN,
        },
    ],
        RetryConfig("backoff", BackoffStrategy(1, 50, 1.1, 100), False))

    # Use the SDK ...

```

If you'd like to override the default retry strategy for all operations that support retries, you can use the `retry_config` optional parameter when initializing the SDK:
```python
from mammoth_analytics import MammothAnalytics, models
from mammoth_analytics.utils import BackoffStrategy, RetryConfig
import os


with MammothAnalytics(
    server_url="https://api.example.com",
    retry_config=RetryConfig("backoff", BackoffStrategy(1, 50, 1.1, 100), False),
    security=models.Security(
        api_key=os.getenv("MAMMOTHANALYTICS_API_KEY", ""),
        api_secret=os.getenv("MAMMOTHANALYTICS_API_SECRET", ""),
    ),
) as ma_client:

    ma_client.projects.add_user(workspace_id=4, project_id=4, users=[
        {
            "user_id": 4,
            "role_name": models.RoleName.PROJECT_ADMIN,
        },
    ])

    # Use the SDK ...

```
<!-- End Retries [retries] -->

<!-- Start Error Handling [errors] -->
## Error Handling

[`MammothAnalyticsError`](./src/mammoth_analytics/errors/mammothanalyticserror.py) is the base class for all HTTP error responses. It has the following properties:

| Property           | Type             | Description                                                                             |
| ------------------ | ---------------- | --------------------------------------------------------------------------------------- |
| `err.message`      | `str`            | Error message                                                                           |
| `err.status_code`  | `int`            | HTTP response status code eg `404`                                                      |
| `err.headers`      | `httpx.Headers`  | HTTP response headers                                                                   |
| `err.body`         | `str`            | HTTP body. Can be empty string if no body is returned.                                  |
| `err.raw_response` | `httpx.Response` | Raw HTTP response                                                                       |
| `err.data`         |                  | Optional. Some errors may contain structured data. [See Error Classes](#error-classes). |

### Example
```python
from mammoth_analytics import MammothAnalytics, errors, models
import os


with MammothAnalytics(
    server_url="https://api.example.com",
    security=models.Security(
        api_key=os.getenv("MAMMOTHANALYTICS_API_KEY", ""),
        api_secret=os.getenv("MAMMOTHANALYTICS_API_SECRET", ""),
    ),
) as ma_client:

    try:

        ma_client.projects.remove_all(workspace_id=4, ids="1,2,3")

        # Use the SDK ...


    except errors.MammothAnalyticsError as e:
        # The base class for HTTP error responses
        print(e.message)
        print(e.status_code)
        print(e.body)
        print(e.headers)
        print(e.raw_response)

        # Depending on the method different errors may be thrown
        if isinstance(e, errors.DeleteProjectsResponseBodyError1):
            print(e.data.status_code)  # int
            print(e.data.detail)  # str
            print(e.data.extra)  # OptionalNullable[models.DeleteProjectsBadRequestExtra1]
```

### Error Classes
**Primary error:**
* [`MammothAnalyticsError`](./src/mammoth_analytics/errors/mammothanalyticserror.py): The base class for HTTP error responses.

<details><summary>Less common errors (238)</summary>

<br />

**Network errors:**
* [`httpx.RequestError`](https://www.python-httpx.org/exceptions/#httpx.RequestError): Base class for request errors.
    * [`httpx.ConnectError`](https://www.python-httpx.org/exceptions/#httpx.ConnectError): HTTP client was unable to make a request to a server.
    * [`httpx.TimeoutException`](https://www.python-httpx.org/exceptions/#httpx.TimeoutException): HTTP request timed out.


**Inherit from [`MammothAnalyticsError`](./src/mammoth_analytics/errors/mammothanalyticserror.py)**:
* [`DeleteProjectsResponseBodyError1`](./src/mammoth_analytics/errors/deleteprojectsresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteProjectsResponseBodyError2`](./src/mammoth_analytics/errors/deleteprojectsresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateProjectsResponseBodyError1`](./src/mammoth_analytics/errors/updateprojectsresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateProjectsResponseBodyError2`](./src/mammoth_analytics/errors/updateprojectsresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`ListDataviewsResponseBodyError1`](./src/mammoth_analytics/errors/listdataviewsresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`ListDataviewsResponseBodyError2`](./src/mammoth_analytics/errors/listdataviewsresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`AddDataviewResponseBodyError1`](./src/mammoth_analytics/errors/adddataviewresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`AddDataviewResponseBodyError2`](./src/mammoth_analytics/errors/adddataviewresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteMultipleDataviewsResponseBodyError1`](./src/mammoth_analytics/errors/deletemultipledataviewsresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteMultipleDataviewsResponseBodyError2`](./src/mammoth_analytics/errors/deletemultipledataviewsresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetDataviewInformationIndividualResponseBodyError1`](./src/mammoth_analytics/errors/getdataviewinformationindividualresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetDataviewInformationIndividualResponseBodyError2`](./src/mammoth_analytics/errors/getdataviewinformationindividualresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteDataviewResponseBodyError1`](./src/mammoth_analytics/errors/deletedataviewresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteDataviewResponseBodyError2`](./src/mammoth_analytics/errors/deletedataviewresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`PatchResponseBodyError1`](./src/mammoth_analytics/errors/patchresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`PatchResponseBodyError2`](./src/mammoth_analytics/errors/patchresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetActiveUsersResponseBodyError1`](./src/mammoth_analytics/errors/getactiveusersresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetActiveUsersResponseBodyError2`](./src/mammoth_analytics/errors/getactiveusersresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`MarkActiveUserResponseBodyError1`](./src/mammoth_analytics/errors/markactiveuserresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`MarkActiveUserResponseBodyError2`](./src/mammoth_analytics/errors/markactiveuserresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetDataviewDataResponseBodyError1`](./src/mammoth_analytics/errors/getdataviewdataresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetDataviewDataResponseBodyError2`](./src/mammoth_analytics/errors/getdataviewdataresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetDataviewDataPostResponseBodyError1`](./src/mammoth_analytics/errors/getdataviewdatapostresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetDataviewDataPostResponseBodyError2`](./src/mammoth_analytics/errors/getdataviewdatapostresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`AiSuggestionsResponseBodyError1`](./src/mammoth_analytics/errors/aisuggestionsresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`AiSuggestionsResponseBodyError2`](./src/mammoth_analytics/errors/aisuggestionsresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GenerateProfileResponseBodyError1`](./src/mammoth_analytics/errors/generateprofileresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`GenerateProfileResponseBodyError2`](./src/mammoth_analytics/errors/generateprofileresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetValidationInfoResponseBodyError1`](./src/mammoth_analytics/errors/getvalidationinforesponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetValidationInfoResponseBodyError2`](./src/mammoth_analytics/errors/getvalidationinforesponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`PreviewResponseBodyError1`](./src/mammoth_analytics/errors/previewresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`PreviewResponseBodyError2`](./src/mammoth_analytics/errors/previewresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetPipelineResponseBodyError1`](./src/mammoth_analytics/errors/getpipelineresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetPipelineResponseBodyError2`](./src/mammoth_analytics/errors/getpipelineresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`EditPipelineResponseBodyError1`](./src/mammoth_analytics/errors/editpipelineresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`EditPipelineResponseBodyError2`](./src/mammoth_analytics/errors/editpipelineresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetPipelineTasksResponseBodyError1`](./src/mammoth_analytics/errors/getpipelinetasksresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetPipelineTasksResponseBodyError2`](./src/mammoth_analytics/errors/getpipelinetasksresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`AddTaskResponseBodyError1`](./src/mammoth_analytics/errors/addtaskresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`AddTaskResponseBodyError2`](./src/mammoth_analytics/errors/addtaskresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetPipelineTaskResponseBodyError1`](./src/mammoth_analytics/errors/getpipelinetaskresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetPipelineTaskResponseBodyError2`](./src/mammoth_analytics/errors/getpipelinetaskresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteTaskResponseBodyError1`](./src/mammoth_analytics/errors/deletetaskresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteTaskResponseBodyError2`](./src/mammoth_analytics/errors/deletetaskresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`EditTaskResponseBodyError1`](./src/mammoth_analytics/errors/edittaskresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`EditTaskResponseBodyError2`](./src/mammoth_analytics/errors/edittaskresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetPipelineExportsResponseBodyError1`](./src/mammoth_analytics/errors/getpipelineexportsresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetPipelineExportsResponseBodyError2`](./src/mammoth_analytics/errors/getpipelineexportsresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`AddExportResponseBodyError1`](./src/mammoth_analytics/errors/addexportresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`AddExportResponseBodyError2`](./src/mammoth_analytics/errors/addexportresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetPipelineExportResponseBodyError1`](./src/mammoth_analytics/errors/getpipelineexportresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetPipelineExportResponseBodyError2`](./src/mammoth_analytics/errors/getpipelineexportresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`EditExportResponseBodyError1`](./src/mammoth_analytics/errors/editexportresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`EditExportResponseBodyError2`](./src/mammoth_analytics/errors/editexportresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteExportResponseBodyError1`](./src/mammoth_analytics/errors/deleteexportresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteExportResponseBodyError2`](./src/mammoth_analytics/errors/deleteexportresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetPipelineItemsResponseBodyError1`](./src/mammoth_analytics/errors/getpipelineitemsresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetPipelineItemsResponseBodyError2`](./src/mammoth_analytics/errors/getpipelineitemsresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetKeysByWorkspaceIDResponseBodyError1`](./src/mammoth_analytics/errors/getkeysbyworkspaceidresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetKeysByWorkspaceIDResponseBodyError2`](./src/mammoth_analytics/errors/getkeysbyworkspaceidresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetExternalKeyResponseBodyError1`](./src/mammoth_analytics/errors/getexternalkeyresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetExternalKeyResponseBodyError2`](./src/mammoth_analytics/errors/getexternalkeyresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteUserDataBadRequestError`](./src/mammoth_analytics/errors/deleteuserdatabadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`ShopifyCustomerRedactBadRequestError`](./src/mammoth_analytics/errors/shopifycustomerredactbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`ShopifyDataRequestBadRequestError`](./src/mammoth_analytics/errors/shopifydatarequestbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`ShopifyShopRedactBadRequestError`](./src/mammoth_analytics/errors/shopifyshopredactbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`BrowseResourcesBadRequestError`](./src/mammoth_analytics/errors/browseresourcesbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`BrowseFolderFoldersBadRequestError`](./src/mammoth_analytics/errors/browsefolderfoldersbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`BrowseProjectProjectsBadRequestError`](./src/mammoth_analytics/errors/browseprojectprojectsbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`BrowseWorkspaceWorkspacesBadRequestError`](./src/mammoth_analytics/errors/browseworkspaceworkspacesbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`RegisterSubscriptionBadRequestError`](./src/mammoth_analytics/errors/registersubscriptionbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateSubscriptionBadRequestError`](./src/mammoth_analytics/errors/updatesubscriptionbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`ArchivePlanBadRequestError`](./src/mammoth_analytics/errors/archiveplanbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`CreatePlanBadRequestError`](./src/mammoth_analytics/errors/createplanbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetPlanBadRequestError`](./src/mammoth_analytics/errors/getplanbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdatePlanBadRequestError`](./src/mammoth_analytics/errors/updateplanbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeletePlanBadRequestError`](./src/mammoth_analytics/errors/deleteplanbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateStorageTiersBadRequestError`](./src/mammoth_analytics/errors/updatestoragetiersbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`CreateConnectorBadRequestError`](./src/mammoth_analytics/errors/createconnectorbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateConnectorBadRequestError`](./src/mammoth_analytics/errors/updateconnectorbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteConnectorBadRequestError`](./src/mammoth_analytics/errors/deleteconnectorbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`CreateFeatureBadRequestError`](./src/mammoth_analytics/errors/createfeaturebadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateFeatureBadRequestError`](./src/mammoth_analytics/errors/updatefeaturebadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteFeatureBadRequestError`](./src/mammoth_analytics/errors/deletefeaturebadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`AddConnectorToProfileBadRequestError`](./src/mammoth_analytics/errors/addconnectortoprofilebadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`CreateConnectorProfileBadRequestError`](./src/mammoth_analytics/errors/createconnectorprofilebadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateConnectorProfileBadRequestError`](./src/mammoth_analytics/errors/updateconnectorprofilebadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteConnectorProfileBadRequestError`](./src/mammoth_analytics/errors/deleteconnectorprofilebadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`AddFeatureToProfileBadRequestError`](./src/mammoth_analytics/errors/addfeaturetoprofilebadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`CreateFeatureProfileBadRequestError`](./src/mammoth_analytics/errors/createfeatureprofilebadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateFeatureProfileBadRequestError`](./src/mammoth_analytics/errors/updatefeatureprofilebadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteFeatureProfileBadRequestError`](./src/mammoth_analytics/errors/deletefeatureprofilebadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`CancelWorkspaceSubscriptionBadRequestError`](./src/mammoth_analytics/errors/cancelworkspacesubscriptionbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`CreateCheckoutURLBadRequestError`](./src/mammoth_analytics/errors/createcheckouturlbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`CreateCustomerPortalURLBadRequestError`](./src/mammoth_analytics/errors/createcustomerportalurlbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetWorkspaceSubscriptionBadRequestError`](./src/mammoth_analytics/errors/getworkspacesubscriptionbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`CreateWorkspaceSubscriptionBadRequestError`](./src/mammoth_analytics/errors/createworkspacesubscriptionbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetPaymentMethodsBadRequestError`](./src/mammoth_analytics/errors/getpaymentmethodsbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetUpcomingInvoiceBadRequestError`](./src/mammoth_analytics/errors/getupcominginvoicebadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetWorkspaceBillingHistoryBadRequestError`](./src/mammoth_analytics/errors/getworkspacebillinghistorybadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetWorkspaceSubscriptionStatusBadRequestError`](./src/mammoth_analytics/errors/getworkspacesubscriptionstatusbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetWorkspaceUsageBadRequestError`](./src/mammoth_analytics/errors/getworkspaceusagebadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`CheckConnectorAccessBadRequestError`](./src/mammoth_analytics/errors/checkconnectoraccessbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`CheckFeatureAccessBadRequestError`](./src/mammoth_analytics/errors/checkfeatureaccessbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`CheckUsageLimitsBadRequestError`](./src/mammoth_analytics/errors/checkusagelimitsbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`CreateDatasetsBadRequestError`](./src/mammoth_analytics/errors/createdatasetsbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteDatasetsBadRequestError`](./src/mammoth_analytics/errors/deletedatasetsbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateDatasetsBadRequestError`](./src/mammoth_analytics/errors/updatedatasetsbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteDatasetBadRequestError`](./src/mammoth_analytics/errors/deletedatasetbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateDatasetBadRequestError`](./src/mammoth_analytics/errors/updatedatasetbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetDatasetDataBadRequestError`](./src/mammoth_analytics/errors/getdatasetdatabadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetBatchesBadRequestError`](./src/mammoth_analytics/errors/getbatchesbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`CreateBatchResponseBodyError1`](./src/mammoth_analytics/errors/createbatchresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`CreateBatchResponseBodyError2`](./src/mammoth_analytics/errors/createbatchresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteBatchesResponseBodyError1`](./src/mammoth_analytics/errors/deletebatchesresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteBatchesResponseBodyError2`](./src/mammoth_analytics/errors/deletebatchesresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateBatchesResponseBodyError1`](./src/mammoth_analytics/errors/updatebatchesresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateBatchesResponseBodyError2`](./src/mammoth_analytics/errors/updatebatchesresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetBatchBadRequestError`](./src/mammoth_analytics/errors/getbatchbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteBatchResponseBodyError1`](./src/mammoth_analytics/errors/deletebatchresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteBatchResponseBodyError2`](./src/mammoth_analytics/errors/deletebatchresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`RemoveUserFromWorkspaceBadRequestError`](./src/mammoth_analytics/errors/removeuserfromworkspacebadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateUserToWorkspaceBadRequestError`](./src/mammoth_analytics/errors/updateusertoworkspacebadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`CreateWorkspaceBadRequestError`](./src/mammoth_analytics/errors/createworkspacebadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteUserWorkspaceBadRequestError`](./src/mammoth_analytics/errors/deleteuserworkspacebadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`RemoveUserBadRequestError`](./src/mammoth_analytics/errors/removeuserbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`UploadProfilePicResponseBodyError1`](./src/mammoth_analytics/errors/uploadprofilepicresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`UploadProfilePicResponseBodyError2`](./src/mammoth_analytics/errors/uploadprofilepicresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteAvatarBadRequestError`](./src/mammoth_analytics/errors/deleteavatarbadrequesterror.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteSelfResponseBodyError1`](./src/mammoth_analytics/errors/deleteselfresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteSelfResponseBodyError2`](./src/mammoth_analytics/errors/deleteselfresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateUserResponseBodyError1`](./src/mammoth_analytics/errors/updateuserresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateUserResponseBodyError2`](./src/mammoth_analytics/errors/updateuserresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteScheduleResponseBodyError1`](./src/mammoth_analytics/errors/deletescheduleresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteScheduleResponseBodyError2`](./src/mammoth_analytics/errors/deletescheduleresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteDsConfigsResponseBodyError1`](./src/mammoth_analytics/errors/deletedsconfigsresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteDsConfigsResponseBodyError2`](./src/mammoth_analytics/errors/deletedsconfigsresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteDsConfigResponseBodyError1`](./src/mammoth_analytics/errors/deletedsconfigresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteDsConfigResponseBodyError2`](./src/mammoth_analytics/errors/deletedsconfigresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateDsConfigsResponseBodyError1`](./src/mammoth_analytics/errors/updatedsconfigsresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateDsConfigsResponseBodyError2`](./src/mammoth_analytics/errors/updatedsconfigsresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`ListDsConfigsResponseBodyError1`](./src/mammoth_analytics/errors/listdsconfigsresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`ListDsConfigsResponseBodyError2`](./src/mammoth_analytics/errors/listdsconfigsresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`ValidateAndGetDsConfigResponseBodyError1`](./src/mammoth_analytics/errors/validateandgetdsconfigresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`ValidateAndGetDsConfigResponseBodyError2`](./src/mammoth_analytics/errors/validateandgetdsconfigresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetConnectionResponseBodyError1`](./src/mammoth_analytics/errors/getconnectionresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetConnectionResponseBodyError2`](./src/mammoth_analytics/errors/getconnectionresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteConnectionResponseBodyError1`](./src/mammoth_analytics/errors/deleteconnectionresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteConnectionResponseBodyError2`](./src/mammoth_analytics/errors/deleteconnectionresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateConnectionResponseBodyError1`](./src/mammoth_analytics/errors/updateconnectionresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateConnectionResponseBodyError2`](./src/mammoth_analytics/errors/updateconnectionresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`SaveConnectionResponseBodyError1`](./src/mammoth_analytics/errors/saveconnectionresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`SaveConnectionResponseBodyError2`](./src/mammoth_analytics/errors/saveconnectionresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`CreateAWebhookResponseBodyError1`](./src/mammoth_analytics/errors/createawebhookresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`CreateAWebhookResponseBodyError2`](./src/mammoth_analytics/errors/createawebhookresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteWebhookResponseBodyError1`](./src/mammoth_analytics/errors/deletewebhookresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteWebhookResponseBodyError2`](./src/mammoth_analytics/errors/deletewebhookresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateWebhookConfigurationsResponseBodyError1`](./src/mammoth_analytics/errors/updatewebhookconfigurationsresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateWebhookConfigurationsResponseBodyError2`](./src/mammoth_analytics/errors/updatewebhookconfigurationsresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`AddDataToWebhookResponseBodyError1`](./src/mammoth_analytics/errors/adddatatowebhookresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`AddDataToWebhookResponseBodyError2`](./src/mammoth_analytics/errors/adddatatowebhookresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteFilesResponseBodyError1`](./src/mammoth_analytics/errors/deletefilesresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteFilesResponseBodyError2`](./src/mammoth_analytics/errors/deletefilesresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteFileResponseBodyError1`](./src/mammoth_analytics/errors/deletefileresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteFileResponseBodyError2`](./src/mammoth_analytics/errors/deletefileresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateUserPreferencesResponseBodyError1`](./src/mammoth_analytics/errors/updateuserpreferencesresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateUserPreferencesResponseBodyError2`](./src/mammoth_analytics/errors/updateuserpreferencesresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteFoldersResponseBodyError1`](./src/mammoth_analytics/errors/deletefoldersresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteFoldersResponseBodyError2`](./src/mammoth_analytics/errors/deletefoldersresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteFolderResponseBodyError1`](./src/mammoth_analytics/errors/deletefolderresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteFolderResponseBodyError2`](./src/mammoth_analytics/errors/deletefolderresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteAutomationResponseBodyError1`](./src/mammoth_analytics/errors/deleteautomationresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteAutomationResponseBodyError2`](./src/mammoth_analytics/errors/deleteautomationresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetChatStatusResponseBodyError1`](./src/mammoth_analytics/errors/getchatstatusresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetChatStatusResponseBodyError2`](./src/mammoth_analytics/errors/getchatstatusresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetQuerySuggestionResponseBodyError1`](./src/mammoth_analytics/errors/getquerysuggestionresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetQuerySuggestionResponseBodyError2`](./src/mammoth_analytics/errors/getquerysuggestionresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateSegmentsResponseBodyError1`](./src/mammoth_analytics/errors/updatesegmentsresponsebodyerror1.py): Client Error. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateSegmentsResponseBodyError2`](./src/mammoth_analytics/errors/updatesegmentsresponsebodyerror2.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`ListUsersOfWorkspacesBadRequestError`](./src/mammoth_analytics/errors/listusersofworkspacesbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`TransferOwnershipsBadRequestError`](./src/mammoth_analytics/errors/transferownershipsbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`GetConditionalFormatBadRequestError`](./src/mammoth_analytics/errors/getconditionalformatbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteConditionalFormatBadRequestError`](./src/mammoth_analytics/errors/deleteconditionalformatbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`UpdateConditionalFormatBadRequestError`](./src/mammoth_analytics/errors/updateconditionalformatbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`CreateConditionalFormatBadRequestError`](./src/mammoth_analytics/errors/createconditionalformatbadrequesterror.py): Validation Exception. Status code `400`. Applicable to 1 of 213 methods.*
* [`DeleteProjectsUnauthorizedError`](./src/mammoth_analytics/errors/deleteprojectsunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`UpdateProjectsUnauthorizedError`](./src/mammoth_analytics/errors/updateprojectsunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`ListDataviewsUnauthorizedError`](./src/mammoth_analytics/errors/listdataviewsunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`AddDataviewUnauthorizedError`](./src/mammoth_analytics/errors/adddataviewunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`DeleteMultipleDataviewsUnauthorizedError`](./src/mammoth_analytics/errors/deletemultipledataviewsunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`GetDataviewInformationIndividualUnauthorizedError`](./src/mammoth_analytics/errors/getdataviewinformationindividualunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`DeleteDataviewUnauthorizedError`](./src/mammoth_analytics/errors/deletedataviewunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`PatchUnauthorizedError`](./src/mammoth_analytics/errors/patchunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`GetActiveUsersUnauthorizedError`](./src/mammoth_analytics/errors/getactiveusersunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`MarkActiveUserUnauthorizedError`](./src/mammoth_analytics/errors/markactiveuserunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`GetDataviewDataUnauthorizedError`](./src/mammoth_analytics/errors/getdataviewdataunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`GetDataviewDataPostUnauthorizedError`](./src/mammoth_analytics/errors/getdataviewdatapostunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`GenerateSQLUnauthorizedError`](./src/mammoth_analytics/errors/generatesqlunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`GenerateProfileUnauthorizedError`](./src/mammoth_analytics/errors/generateprofileunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`GetPipelineItemsUnauthorizedError`](./src/mammoth_analytics/errors/getpipelineitemsunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`UploadProfilePicUnauthorizedError`](./src/mammoth_analytics/errors/uploadprofilepicunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`DeleteAvatarUnauthorizedError`](./src/mammoth_analytics/errors/deleteavatarunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`DeleteSelfUnauthorizedError`](./src/mammoth_analytics/errors/deleteselfunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`UpdateUserUnauthorizedError`](./src/mammoth_analytics/errors/updateuserunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`DeleteScheduleUnauthorizedError`](./src/mammoth_analytics/errors/deletescheduleunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`GetConnectionUnauthorizedError`](./src/mammoth_analytics/errors/getconnectionunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`DeleteConnectionUnauthorizedError`](./src/mammoth_analytics/errors/deleteconnectionunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`UpdateConnectionUnauthorizedError`](./src/mammoth_analytics/errors/updateconnectionunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`SaveConnectionUnauthorizedError`](./src/mammoth_analytics/errors/saveconnectionunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`DeleteAutomationUnauthorizedError`](./src/mammoth_analytics/errors/deleteautomationunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`GetChatStatusUnauthorizedError`](./src/mammoth_analytics/errors/getchatstatusunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`GetQuerySuggestionUnauthorizedError`](./src/mammoth_analytics/errors/getquerysuggestionunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`UpdateSegmentsUnauthorizedError`](./src/mammoth_analytics/errors/updatesegmentsunauthorizederror.py): Authorization Exception. Status code `401`. Applicable to 1 of 213 methods.*
* [`ListDataviewsNotFoundError`](./src/mammoth_analytics/errors/listdataviewsnotfounderror.py): Not Found Exception. Status code `404`. Applicable to 1 of 213 methods.*
* [`AddDataviewNotFoundError`](./src/mammoth_analytics/errors/adddataviewnotfounderror.py): Not Found Exception. Status code `404`. Applicable to 1 of 213 methods.*
* [`DeleteMultipleDataviewsNotFoundError`](./src/mammoth_analytics/errors/deletemultipledataviewsnotfounderror.py): Not Found Exception. Status code `404`. Applicable to 1 of 213 methods.*
* [`GetDataviewInformationIndividualNotFoundError`](./src/mammoth_analytics/errors/getdataviewinformationindividualnotfounderror.py): Not Found Exception. Status code `404`. Applicable to 1 of 213 methods.*
* [`DeleteDataviewNotFoundError`](./src/mammoth_analytics/errors/deletedataviewnotfounderror.py): Not Found Exception. Status code `404`. Applicable to 1 of 213 methods.*
* [`PatchNotFoundError`](./src/mammoth_analytics/errors/patchnotfounderror.py): Not Found Exception. Status code `404`. Applicable to 1 of 213 methods.*
* [`GetActiveUsersNotFoundError`](./src/mammoth_analytics/errors/getactiveusersnotfounderror.py): Not Found Exception. Status code `404`. Applicable to 1 of 213 methods.*
* [`MarkActiveUserNotFoundError`](./src/mammoth_analytics/errors/markactiveusernotfounderror.py): Not Found Exception. Status code `404`. Applicable to 1 of 213 methods.*
* [`GetDataviewDataNotFoundError`](./src/mammoth_analytics/errors/getdataviewdatanotfounderror.py): Not Found Exception. Status code `404`. Applicable to 1 of 213 methods.*
* [`GetDataviewDataPostNotFoundError`](./src/mammoth_analytics/errors/getdataviewdatapostnotfounderror.py): Not Found Exception. Status code `404`. Applicable to 1 of 213 methods.*
* [`GetPipelineNotFoundError`](./src/mammoth_analytics/errors/getpipelinenotfounderror.py): Not Found Exception. Status code `404`. Applicable to 1 of 213 methods.*
* [`EditPipelineNotFoundError`](./src/mammoth_analytics/errors/editpipelinenotfounderror.py): Not Found Exception. Status code `404`. Applicable to 1 of 213 methods.*
* [`GetPipelineTaskNotFoundError`](./src/mammoth_analytics/errors/getpipelinetasknotfounderror.py): Not Found Exception. Status code `404`. Applicable to 1 of 213 methods.*
* [`DeleteTaskNotFoundError`](./src/mammoth_analytics/errors/deletetasknotfounderror.py): Not Found Exception. Status code `404`. Applicable to 1 of 213 methods.*
* [`EditTaskNotFoundError`](./src/mammoth_analytics/errors/edittasknotfounderror.py): Not Found Exception. Status code `404`. Applicable to 1 of 213 methods.*
* [`GetPipelineExportNotFoundError`](./src/mammoth_analytics/errors/getpipelineexportnotfounderror.py): Not Found Exception. Status code `404`. Applicable to 1 of 213 methods.*
* [`EditExportNotFoundError`](./src/mammoth_analytics/errors/editexportnotfounderror.py): Not Found Exception. Status code `404`. Applicable to 1 of 213 methods.*
* [`DeleteExportNotFoundError`](./src/mammoth_analytics/errors/deleteexportnotfounderror.py): Not Found Exception. Status code `404`. Applicable to 1 of 213 methods.*
* [`GetPipelineItemsNotFoundError`](./src/mammoth_analytics/errors/getpipelineitemsnotfounderror.py): Not Found Exception. Status code `404`. Applicable to 1 of 213 methods.*
* [`GetExternalKeyNotFoundError`](./src/mammoth_analytics/errors/getexternalkeynotfounderror.py): Not Found Exception. Status code `404`. Applicable to 1 of 213 methods.*
* [`ResponseValidationError`](./src/mammoth_analytics/errors/responsevalidationerror.py): Type mismatch between the response data and the expected Pydantic model. Provides access to the Pydantic validation error via the `cause` attribute.

</details>

\* Check [the method documentation](#available-resources-and-operations) to see if the error is applicable.
<!-- End Error Handling [errors] -->

<!-- Start Custom HTTP Client [http-client] -->
## Custom HTTP Client

The Python SDK makes API calls using the [httpx](https://www.python-httpx.org/) HTTP library.  In order to provide a convenient way to configure timeouts, cookies, proxies, custom headers, and other low-level configuration, you can initialize the SDK client with your own HTTP client instance.
Depending on whether you are using the sync or async version of the SDK, you can pass an instance of `HttpClient` or `AsyncHttpClient` respectively, which are Protocol's ensuring that the client has the necessary methods to make API calls.
This allows you to wrap the client with your own custom logic, such as adding custom headers, logging, or error handling, or you can just pass an instance of `httpx.Client` or `httpx.AsyncClient` directly.

For example, you could specify a header for every request that this sdk makes as follows:
```python
from mammoth_analytics import MammothAnalytics
import httpx

http_client = httpx.Client(headers={"x-custom-header": "someValue"})
s = MammothAnalytics(client=http_client)
```

or you could wrap the client with your own custom logic:
```python
from mammoth_analytics import MammothAnalytics
from mammoth_analytics.httpclient import AsyncHttpClient
import httpx

class CustomClient(AsyncHttpClient):
    client: AsyncHttpClient

    def __init__(self, client: AsyncHttpClient):
        self.client = client

    async def send(
        self,
        request: httpx.Request,
        *,
        stream: bool = False,
        auth: Union[
            httpx._types.AuthTypes, httpx._client.UseClientDefault, None
        ] = httpx.USE_CLIENT_DEFAULT,
        follow_redirects: Union[
            bool, httpx._client.UseClientDefault
        ] = httpx.USE_CLIENT_DEFAULT,
    ) -> httpx.Response:
        request.headers["Client-Level-Header"] = "added by client"

        return await self.client.send(
            request, stream=stream, auth=auth, follow_redirects=follow_redirects
        )

    def build_request(
        self,
        method: str,
        url: httpx._types.URLTypes,
        *,
        content: Optional[httpx._types.RequestContent] = None,
        data: Optional[httpx._types.RequestData] = None,
        files: Optional[httpx._types.RequestFiles] = None,
        json: Optional[Any] = None,
        params: Optional[httpx._types.QueryParamTypes] = None,
        headers: Optional[httpx._types.HeaderTypes] = None,
        cookies: Optional[httpx._types.CookieTypes] = None,
        timeout: Union[
            httpx._types.TimeoutTypes, httpx._client.UseClientDefault
        ] = httpx.USE_CLIENT_DEFAULT,
        extensions: Optional[httpx._types.RequestExtensions] = None,
    ) -> httpx.Request:
        return self.client.build_request(
            method,
            url,
            content=content,
            data=data,
            files=files,
            json=json,
            params=params,
            headers=headers,
            cookies=cookies,
            timeout=timeout,
            extensions=extensions,
        )

s = MammothAnalytics(async_client=CustomClient(httpx.AsyncClient()))
```
<!-- End Custom HTTP Client [http-client] -->

<!-- Start Resource Management [resource-management] -->
## Resource Management

The `MammothAnalytics` class implements the context manager protocol and registers a finalizer function to close the underlying sync and async HTTPX clients it uses under the hood. This will close HTTP connections, release memory and free up other resources held by the SDK. In short-lived Python programs and notebooks that make a few SDK method calls, resource management may not be a concern. However, in longer-lived programs, it is beneficial to create a single SDK instance via a [context manager][context-manager] and reuse it across the application.

[context-manager]: https://docs.python.org/3/reference/datamodel.html#context-managers

```python
from mammoth_analytics import MammothAnalytics, models
import os
def main():

    with MammothAnalytics(
        server_url="https://api.example.com",
        security=models.Security(
            api_key=os.getenv("MAMMOTHANALYTICS_API_KEY", ""),
            api_secret=os.getenv("MAMMOTHANALYTICS_API_SECRET", ""),
        ),
    ) as ma_client:
        # Rest of application here...


# Or when using async:
async def amain():

    async with MammothAnalytics(
        server_url="https://api.example.com",
        security=models.Security(
            api_key=os.getenv("MAMMOTHANALYTICS_API_KEY", ""),
            api_secret=os.getenv("MAMMOTHANALYTICS_API_SECRET", ""),
        ),
    ) as ma_client:
        # Rest of application here...
```
<!-- End Resource Management [resource-management] -->

<!-- Start Debugging [debug] -->
## Debugging

You can setup your SDK to emit debug logs for SDK requests and responses.

You can pass your own logger class directly into your SDK.
```python
from mammoth_analytics import MammothAnalytics
import logging

logging.basicConfig(level=logging.DEBUG)
s = MammothAnalytics(server_url="https://example.com", debug_logger=logging.getLogger("mammoth_analytics"))
```

You can also enable a default debug logger by setting an environment variable `MAMMOTHANALYTICS_DEBUG` to true.
<!-- End Debugging [debug] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->

# Development

## Maturity

This SDK is in beta, and there may be breaking changes between versions without a major version update. Therefore, we recommend pinning usage
to a specific package version. This way, you can install the same version each time without breaking changes unless you are intentionally
looking for the latest version.

## Contributions

While we value open-source contributions to this SDK, this library is generated programmatically. Any manual changes added to internal files will be overwritten on the next generation. 
We look forward to hearing your feedback. Feel free to open a PR or an issue with a proof of concept and we'll do our best to include it in a future release. 

### SDK Created by [Speakeasy](https://www.speakeasy.com/?utm_source=mammoth-analytics&utm_campaign=python)
