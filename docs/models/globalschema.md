# GlobalSchema


## Fields

| Field                                                                      | Type                                                                       | Required                                                                   | Description                                                                | Example                                                                    |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `self_serve`                                                               | [OptionalNullable[models.SelfServeSchema]](../models/selfserveschema.md)   | :heavy_minus_sign:                                                         | Self Serve                                                                 | {<br/>"value": {<br/>"onboarding_state": "registered"<br/>}<br/>}          |
| `onboarding`                                                               | [OptionalNullable[models.OnboardingSchema]](../models/onboardingschema.md) | :heavy_minus_sign:                                                         | Onboarding                                                                 | {<br/>"value": {<br/>"DATAFLOW_SETTINGS": true<br/>}<br/>}                 |