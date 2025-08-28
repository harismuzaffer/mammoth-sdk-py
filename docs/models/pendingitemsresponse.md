# PendingItemsResponse


## Fields

| Field                                                                         | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `non_sync_items`                                                              | List[[models.PendingItem](../models/pendingitem.md)]                          | :heavy_check_mark:                                                            | N/A                                                                           |
| `pending_data_update_items`                                                   | List[[models.PendingItem](../models/pendingitem.md)]                          | :heavy_check_mark:                                                            | N/A                                                                           |
| `pending_changes`                                                             | Dict[str, [models.PendingPipelineChange](../models/pendingpipelinechange.md)] | :heavy_check_mark:                                                            | N/A                                                                           |