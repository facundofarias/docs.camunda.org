---

title: 'Execute Filter Single Result (POST)'
category: 'Filter'

keywords: 'post'

---

Executes the saved query of the filter and returns the single result. This method is slightly more
powerful then the [GET query](ref:#filter-execute-filter-single-result) because it allows to extend
the saved query of the filter.

Method
------

POST `/filter/{id}/singleResult`

Parameters
----------

#### Path Parameters

<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>id</td>
    <td>The id of the filter to execute.</td>
  </tr>
</table>

#### Request Body

A JSON object which corresponds to the type of the saved query of the filter, i.e., if the
resource type of the filter is `Task` the body should form a valid task query corresponding to
the [Task](ref:#task-get-tasks) resource.

Result
------

A JSON object corresponding to the corresponding entity interface in the engine. This depends
on the saved query in the filter. Therefore it is not possible specify a generic result format,
i.e., if the resource type of the filter is `Task` the result will correspond with the Task
interface in the engine.


Response codes
--------------

<table class="table table-striped">
  <tr>
    <th>Code</th>
    <th>Media type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>200</td>
    <td>application/json</td>
    <td>Request successful.</td>
  </tr>
  <tr>
    <td>200</td>
    <td>application/hal+json</td>
    <td>Request successful. In case of an expected <a href="ref:#overview-hypertext-application-language-hal">HAL</code> response.</td>
  </tr>
  <tr>
    <td>204</td>
    <td></td>
    <td>Request successful, but the result was empty.</td>
  </tr>
  <tr>
    <td>400</td>
    <td>application/json</td>
    <td>
      The executed filter returned more than one single result or the extending query was invalid.
      See the <a href="ref:#overview-introduction">Introduction</a> for the error response format.
    </td>
  </tr>
  <tr>
    <td>403</td>
    <td>application/json</td>
    <td>
       The authenticated user is unauthorized to read this filter.
      See the <a href="ref:#overview-introduction">Introduction</a> for the error response format.
    </td>
  </tr>
  <tr>
    <td>404</td>
    <td>application/json</td>
    <td>
      Filter with given id does not exist. See the
      <a href="ref:#overview-introduction">Introduction</a> for the error response format.
    </td>
  </tr>
</table>


Example
-------

#### Request

POST `filter/aTaskFilterId/singleResult`

Request Body:

<div class="alert alert-warning" role="alert">
  <strong>Note:</strong> The examples shows a task filter. So the request body corresponds
  to a task query. For other resource types the request body will differ.
</div>

```json
{
  "assignee": "jonny1",
  "taskDefinitionKey": "aTaskKey"
}
```

#### Response

Status 200.

<div class="alert alert-warning" role="alert">
  <strong>Note:</strong> The examples shows the result of a task filter. So the response corresponds
  to a task, but for other filters the response format will differ.
</div>

```json
{
  "assignee": "jonny1",
  "caseDefinitionId": null,
  "caseExecutionId": null,
  "caseInstanceId": null,
  "created": "2014-09-15T15:45:48",
  "delegationState": null,
  "description": null,
  "due": null,
  "executionId": "aExecutionId",
  "followUp": null,
  "formKey": null,
  "id": "aTaskId",
  "name": "Task 2",
  "owner": null,
  "parentTaskId": null,
  "priority": 50,
  "processDefinitionId": "aProcessId",
  "processInstanceId": "aProcessInstanceId",
  "suspended": false,
  "taskDefinitionKey": "aTaskKey"
}
```
