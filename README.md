# Unofficial API bindings for Elvia's consumer facing APIs

![Build Status](https://github.com/andersem/elvia-python/actions/workflows/ci.yml/badge.svg)

With the Elvia API you can access information about your own power consumption and get the
current grid tariffes in Elvia's power grid. 

## Installation

Install from pip by using:

```
pip install --upgrade elvia_sdk
```

### Requirements

* Python 3.6+

## Using the SDK

Make sure you are using Elvia and have access:

Get token using this guide: https://www.elvia.no/smart-forbruk/alt-om-din-strommaler/slik-gjor-du-det-aktivering-og-bruk-av-elvias-metervalueapi/

Use your newly created token to get metering values:

```python
from elvia_sdk import Elvia
import json

token = "token from elvia.no"

elvia = Elvia(token)
meter_value_client = elvia.meter_value()

print(json.dumps(meter_value_client.get_meter_values(
    {
        "start_time": "2021-12-08T01:00:00",
        "end_time": "2021-12-08T02:00:00",
        "metering_point_ids": ["abc"],
        "include_production": True
    })))
```
