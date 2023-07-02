---
title: Archive queries
description: Here's how to archive queries via Dune API
---

!!! abstract "ENDPOINTS"
    POST /api/v1/query/{{query_id}}/archive
    POST /api/v1/query/{{query_id}}/unarchive

!!! success end "Note" 
    This endpoint is included only in our Premium subscription plans.

THe Archive query endpoints allow archiving a query or vice verse (i.e. setting an archived query back to active state). Archiving removes the query from "My Creation" folder so in a way delete the query. They **do not accept a request body**. They return query id after the operation.

## Example Request in Python

```python
import dotenv
import os
import json
import requests
import pandas as pd
import time

# load .env file
dotenv.load_dotenv('/Users/abc/Documents/Workspace/misc/.env')
# get API key
api_key = os.environ["DUNE_API_KEY"]
# authentiction with api key
headers = {"X-Dune-API-Key": api_key}

query_id = 62608
base_url = f"https://api.dune.com/api/v1/query/{query_id}/archive"
result_response = requests.request("POST", base_url, headers=headers, params=params)
```

## Example Return

```js
{"query_id":62608}
```

## Error Codes
- 400 - Invalid request (e.g. invalid query ID in URL)
- 402 - Reached maximum number of private queries
- 403 - Not allowed to update this query

