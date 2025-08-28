# CustomPromptParams


## Fields

| Field                                                                | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `column_name`                                                        | *str*                                                                | :heavy_check_mark:                                                   | The name of the column to apply extraction on                        |
| `sequence_number`                                                    | *int*                                                                | :heavy_check_mark:                                                   | The sequence order of the extraction rule                            |
| `prompt`                                                             | *OptionalNullable[str]*                                              | :heavy_minus_sign:                                                   | The user-defined prompt for AI-based extraction                      |
| `edit_regex`                                                         | [OptionalNullable[models.EditRegexSpec]](../models/editregexspec.md) | :heavy_minus_sign:                                                   | Optional edited regex pattern details for extraction                 |