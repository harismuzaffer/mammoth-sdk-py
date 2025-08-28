# UnifiedPromptSpec

Parameters required for intent-based extraction or filtering


## Fields

| Field                                                   | Type                                                    | Required                                                | Description                                             |
| ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- |
| `suggestion_type`                                       | [models.SuggestionType](../models/suggestiontype.md)    | :heavy_check_mark:                                      | Type of operation (extraction or conditional filtering) |
| `params`                                                | [models.Params](../models/params.md)                    | :heavy_check_mark:                                      | Encapsulated parameters for the operation               |