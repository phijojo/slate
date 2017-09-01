---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - API

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the IPAAS API! You can use our API to access IPAAS API endpoints, which can get information on various actions on our Platform.


# Authentication

> To authorize

```

Method: POST

URL : http://10.10.10.24/oauth/token

Body : 

grant_type:client_credentials
client_id: <Client_id>
client_secret: <Secret>

Response:
{
    "access_token": "bd0ae6f6681f964397475c91e3f2790715879a2ab371433dd92eb09cbcb9382b",
    "token_type": "bearer",
    "expires_in": 3600,
    "created_at": 1504124722
}

```

> Make sure to replace `client_id and Secret` with your Client id and Client_secret key.

This will provide you Access_token. IPAAS uses Access_token to allow access to the API.

IPAAS expects for the Access_token to be included in all API requests to the server in a Body that looks like the following:

`access_token: bd0ae6f6681f964397475c91e3f2790715879a2ab371433dd92eb09cbcb9382b`

<aside class="notice">
You must replace <code>client_id and Secret</code> with your personal client_id and Secret key.
</aside>

# IPAAS

## Get All Instance 

```API
Method GET

http://10.10.10.24/openstack/instances?access_token=<access_token>


```

> The above command returns JSON structured like this:

```json
{
    "status": 200,
    "message": "success",
    "data": {
        "stack_r-o7990p62": [
            {
                "uid": "ce90ce43-b4fc-4b64-afe8-af477380cd1f",
                "ip": "10.0.0.237"
            },
            {
                "uid": "513438d3-e5c0-454a-aabf-937baaeacab1",
                "ip": "10.0.0.236"
            }
        ]
    }
}
```

This endpoint retrieves all Instances.

### HTTP Request

`GET http://10.10.10.24/openstack/instances`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token| Yes |  This is a mandatory



## Create  instances

This endpoint creates Instances based on the count, flavor and images.


```API
Method POST

http://10.10.10.24/openstack/compute


```

> The above command returns JSON structured like this:


```json
{"status":200,"message":"success","data":{}}

```

### HTTP Request

`http://10.10.10.24/openstack/compute`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token| Yes |  This is a mandatory
user_name: | Yes | Openstack user ,This is a mandatory
project_name |Yes | Openstack Project ,This is a mandatory
image_id: | Yes | Image id ,This is a mandatory
flavor_id: | Yes | Flavor id ,This is a mandatory
instance_count| Yes |Number of instance ,This is a mandatory
floating_ip |Yes| Floating ip requied or not,This is a mandatory


<aside class="notice">
This is a webhook api
</aside>

## Delete  instances

This endpoint Delete Instances based on the stack.


```API
Method Delete

http://10.10.10.24/openstack/delete_instances?access_token=bd0ae6f6681f964397475c91e3f2790715879a2ab371433dd92eb09cbcb9382b&project_name=devel&stack_name=stack_r-6tc4gha8

```

> The above command returns JSON structured like this:


```json
{"status":200,"message":"success","data":{}}

```

### HTTP Request

`http://10.10.10.24/openstack/delete_instances`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token| Yes |  This is a mandatory
stack_name: | Yes | Stack details ,This is a mandatory
project_name |Yes | Openstack Project ,This is a mandatory






## Billing  instances

Get the instance status


```API
Method GET

http://10.10.10.24/openstack/billing_instances?access_token=bbd0209ba1155eacf76893b3ccca5d6dfe629f86a1218b18b37c6229df860ef3&project_name=devel

```

> The above command returns JSON structured like this:


```json
{
    "status": 200,
    "message": "success",
    "data": {
        "instances": [
            {
                "id": "ecbe45c1-c8c8-464d-b3f2-d0598a8ea3e9",
                "name": "instance_20170901141504290348-2",
                "state": "ACTIVE",
                "created": "2017-09-01T18:25:49.000Z"
            },
            {
                "id": "7207f06a-5c21-4fa9-bd4b-5814dc399c18",
                "name": "instance_20170901141504290348-1",
                "state": "ACTIVE",
                "created": "2017-09-01T18:25:49.000Z"
            },
            {
                "id": "ce90ce43-b4fc-4b64-afe8-af477380cd1f",
                "name": "instance_20170901141504289398-2",
                "state": "ACTIVE",
                "created": "2017-09-01T18:09:59.000Z"
            },
            {
                "id": "513438d3-e5c0-454a-aabf-937baaeacab1",
                "name": "instance_20170901141504289398-1",
                "state": "ACTIVE",
                "created": "2017-09-01T18:09:59.000Z"
            }
        ],
        "total": 4
    }
}

```

### HTTP Request

`http://10.10.10.24/openstack/billing_instances`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token| Yes |  This is a mandatory
project_name |Yes | Openstack Project ,This is a mandatory




