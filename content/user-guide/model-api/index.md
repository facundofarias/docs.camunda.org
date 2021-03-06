---

title: 'Model API'
layout: "section-list"
weight: 80

menu:
  main:
    identifier: "user-guide-model-api"
    parent: "user-guide"

---


The Camunda BPMN model API provides a simple and lightweight library for parsing,
creating, editing and writing of BPMN 2.0 XML files. The model API enables an easy
extraction of information from an existing process definition or to create a
complete new one without manual XML parsing. The BPMN model API is based on a
general XML model API which is useful for general XML processing.

Note: Currently the BPMN model API does not fully support the whole BPMN 2.0 specification.
The list of already supported BPMN 2.0 elements can be found in the source code package {{< javadocref page="index.html?org/camunda/bpm/model/bpmn/instance/package-summary.html" text="org.camunda.bpm.model.bpmn.instance" >}}.
