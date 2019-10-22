The REST API Import service has four different actions available; import, update, delete, and lookup.

Any units imported will be matched on phone or email. If any of these fields matches an existing unit, the unit will not be imported.

Only one unit can be imported with each API call.

An excellent way to test your API calls is to use our Swagger Documentation. You can find this on https://rest.bosbec.io

##### Headers

```
api-key: 00000000-0000-0000-0000-000000000000
content-type: application/json
```

##### Import Unit

```
POST: https://rest.bosbec.io/2/workflows
{
    "workflowid": "00000000-0000-0000-0000-000000000000",
    "metadata": {
        "action": "import",
        "firstname": "John",
        "lastname": "Doe",
        "phone": "+46702000001",
        "email": "john@doe.com",
        "tag": "test"
    },
    "RequestSettings": {
        "content-type":"json",
        "ResponseData": {
            "result": "metadata.result"
        }
    }
}
```

##### Update Unit

```
POST: https://rest.bosbec.io/2/workflows
{
    "workflowid": "00000000-0000-0000-0000-000000000000",
    "metadata": {
        "action": "update",
        "firstname": "John2",
        "lastname": "Doe2",
        "phone": "+46702000002",
        "email": "john@doe.com",
        "tag": "test2"
    },
    "RequestSettings": {
        "content-type":"json",
        "ResponseData": {
            "result": "metadata.result"
        }
    }
}
```

##### Delete Unit

```
POST: https://rest.bosbec.io/2/workflows
{
    "workflowid": "00000000-0000-0000-0000-000000000000",
    "metadata": {
        "action": "delete",
        "phone": "+46702000002",
        "email": "john@doe.com"
    },
    "RequestSettings": {
        "content-type":"json",
        "ResponseData": {
            "result": "metadata.result"
        }
    }
}
```

##### Lookup

```
POST: https://rest.bosbec.io/2/workflows
{
    "workflowid": "00000000-0000-0000-0000-000000000000",
    "metadata": {
        "action": "lookup",
        "phone": "+46702000002"
    },
    "RequestSettings": {
        "content-type":"json",
        "ResponseData": {
            "result": "metadata.result"
        }
    }
}
```
