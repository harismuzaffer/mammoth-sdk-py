<!-- Start SDK Example Usage [usage] -->
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