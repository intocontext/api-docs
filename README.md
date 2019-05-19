# Context API v1 Documentation
## Version: 1.0.0

### Terms of service
http://swagger.io/terms/

**Contact information:**  
info@sweetlabs.io  

**License:** MIT

### Security
**Bearer**  

|apiKey|*API Key*|
|---|---|
|Name|Authorization|
|In|header|

### /v1/public-annotations

#### GET
##### Summary:

Finds public accessible annotations

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| startDate | query |  | No | string |
| endDate | query |  | No | string |
| categories | query |  | No | [ string ] |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | successful operation | [GetAnnotationsResponse](#getannotationsresponse) |
| 404 | No annotations found |  |

### /v1/annotations

#### GET
##### Summary:

Finds organization's private annotations

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| organizationId | query |  | Yes | string |
| startDate | query |  | No | string |
| endDate | query |  | No | string |
| previousStartDate | query |  | No | string |
| previousEndDate | query |  | No | string |
| categories | query |  | No | [ string ] |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | successful operation | [GetAnnotationsResponse](#getannotationsresponse) |
| 404 | No annotations found |  |

##### Security

| Security Schema | Scopes |
| --- | --- |
| Bearer | |

#### POST
##### Summary:

Create an annotation for a concrete organization

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| body | body |  | Yes | [CreateAnnotationRequest](#createannotationrequest) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 201 | Annotation created | [CreateAnnotationResponse](#createannotationresponse) |
| 400 | Bad request |  |

##### Security

| Security Schema | Scopes |
| --- | --- |
| Bearer | |

### /v1/organizations

#### POST
##### Summary:

Create organization for a certain user

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| body | body |  | Yes | [CreateOrganizationRequest](#createorganizationrequest) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 201 | Organization created | [CreateOrganizationResponse](#createorganizationresponse) |
| 400 | Bad request |  |

##### Security

| Security Schema | Scopes |
| --- | --- |
| Bearer | |

#### GET
##### Summary:

Finds organizations for a certain user

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | successful operation | [GetOrganizationsResponse](#getorganizationsresponse) |
| 404 | No organizations found |  |

##### Security

| Security Schema | Scopes |
| --- | --- |
| Bearer | |

### /v1/organizations/{organizationId}

#### PATCH
##### Summary:

Modify organization

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| organizationId | path | Organization id | Yes | string |
| body | body |  | Yes | [CreateOrganizationRequest](#createorganizationrequest) |

##### Responses

| Code | Description |
| ---- | ----------- |
| 204 | Organization modified |
| 400 | Bad request |

##### Security

| Security Schema | Scopes |
| --- | --- |
| Bearer | |

### /v1/organizations/{organizationId}/members

#### GET
##### Summary:

List of organization's members

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| organizationId | path | Organization id | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | successful operation | [GetOrganizationMembersResponse](#getorganizationmembersresponse) |
| 400 | Bad request |  |

##### Security

| Security Schema | Scopes |
| --- | --- |
| Bearer | |

#### POST
##### Summary:

Add member to an organization

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| organizationId | path | Organization id | Yes | string |
| body | body |  | Yes | [AddMemberToOrganizationRequest](#addmembertoorganizationrequest) |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 201 | Member added to organization | [AddMemberToOrganizationResponse](#addmembertoorganizationresponse) |
| 400 | Bad request |  |

##### Security

| Security Schema | Scopes |
| --- | --- |
| Bearer | |

### /v1/organizations/{organizationId}/members/{memberId}

#### DELETE
##### Summary:

Delete organization member

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| organizationId | path | Organization id | Yes | string |
| memberId | path | Member id | Yes | string |

##### Responses

| Code | Description |
| ---- | ----------- |
| 204 | successful operation |
| 400 | Bad request |

##### Security

| Security Schema | Scopes |
| --- | --- |
| Bearer | |

### /v1/event-sources

#### GET
##### Summary:

Finds organization's private event sources

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| organizationId | query |  | Yes | string |
| type | query |  | No | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | successful operation | [GetEventSourcesResponse](#geteventsourcesresponse) |
| 404 | No event sources found |  |

##### Security

| Security Schema | Scopes |
| --- | --- |
| Bearer | |

### Models


#### Annotation

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| _id | string |  | No |
| title | string |  | No |
| category | string |  | No |
| eventSource | object |  | No |
| url | string |  | No |
| description | string |  | No |
| highlighted | boolean |  | No |
| publishDate | string |  | No |
| type | string |  | No |

#### EventSource

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| _id | string |  | No |
| name | string |  | No |
| type | string |  | No |
| scope | string |  | No |
| organization | string | Organization identifier | No |
| insertDate | string |  | No |

#### Organization

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| _id | string |  | No |
| name | string |  | No |

#### Member

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| id | string |  | No |
| userId | string |  | No |
| role | string |  | No |
| email | string |  | No |

#### CreateAnnotationRequest

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| title | string |  | No |
| description | string |  | No |
| eventSourceType | string |  | No |
| url | string |  | No |
| category | string |  | No |
| publishedAt | string |  | No |

#### CreateAnnotationResponse

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| annotation | object |  | No |

#### GetAnnotationsResponse

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| annotations | [ [Annotation](#annotation) ] |  | No |

#### GetEventSourcesResponse

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| eventSource | [ [EventSource](#eventsource) ] |  | No |

#### CreateOrganizationRequest

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| name | string |  | No |

#### CreateOrganizationResponse

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| id | string |  | No |

#### GetOrganizationsResponse

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| organizations | [ [Organization](#organization) ] |  | No |

#### GetOrganizationMembersResponse

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| members | [ [Member](#member) ] |  | No |

#### AddMemberToOrganizationRequest

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| email | string |  | No |
| role | string |  | No |

#### AddMemberToOrganizationResponse

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| id | string |  | No |
| email | string |  | No |
| role | string |  | No |