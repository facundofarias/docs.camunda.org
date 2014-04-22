---

title: 'Post Deployment'
category: 'Deployment'

keywords: 'post create deployment'

---

Create a deployment.

Method
------

POST `/deployment`


Parameters
----------

#### Request Body

A multipart form submit with the following parts:

<table class="table table-striped">
  <tr>
    <th>Form Part Name</th>
    <th>Content Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>deployment-name</td>
    <td>text/plain</td>
    <td>The name for the deployment to be created.</td>
  </tr>
  <tr>
    <td>enable-duplicate-filtering</td>
    <td>text/plain</td>
    <td>
      A flag indicating whether the process engine should perform duplicate checking for the deployment. This allows you to check whether a deployment with the same name and the same resouces already exists and if true, not create a new deployment but instead return the existing deployment. The default value is <code>false</code>.
    </td>
  </tr>
  <tr>
    <td>*</td>
    <td>application/octet-stream</td>
    <td>The binary data to create the deployment resource. It is possible to have more than one form part with different form part names for the binary data to create a deployment.</td>
  </tr>
</table>


Result
------

A json object corresponding to the `Deployment` interface in the engine.
Its properties are as follows:

<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Value</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>links</td>
    <td>List</td>
    <td>Link to the new created deployment with <code>method</code>, <code>href</code> and <code>rel</code>.</td>
  </tr>
  <tr>
    <td>id</td>
    <td>String</td>
    <td>The id of the deployment.</td>
  </tr>
  <tr>
    <td>name</td>
    <td>String</td>
    <td>The name of the deployment.</td>
  </tr>
  <tr>
    <td>deploymentTime</td>
    <td>String</td>
    <td>The time when the deployment was created.</td>
  </tr>
</table>


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
</table>


Example
-------

#### Request

Post data for a new deployment:

POST `/deployment`

```
--28319d96a8c54b529aa9159ad75edef9
Content-Disposition: form-data; name="deployment-name"

aName
--28319d96a8c54b529aa9159ad75edef9
Content-Disposition: form-data; name="enable-duplicate-filtering"

true
--28319d96a8c54b529aa9159ad75edef9
Content-Disposition: form-data; name="data"; filename="test.bpmn"

<?xml version="1.0" encoding="UTF-8"?>
<bpmn2:definitions ...>
  <!-- BPMN 2.0 XML omitted -->
</bpmn2:definitions>
```


#### Response

Status 200.

```json
{
  "links": [
    {
      "method": "GET",
      "href": "http://localhost:38080/rest-test/deployment/aDeploymentId",
      "rel": "self"
    }
  ],
  "id": "aDeploymentId",
  "name": "aName",
  "deploymentTime": "2013-01-23T13:59:43"
}
```