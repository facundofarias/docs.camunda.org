---

title: 'Overview'
category: 'Introduction'

---


Welcome to the camunda BPM userguide! camunda BPM is a Java-based framework for process automation. This document provides information about the features provided by camunda BPM platform.

camunda BPM is built around the process engine component. The following illustration shows the most important components of camunda BPM along with typical user roles.

<center>
  <img class="img-responsive" src="ref:asset:/assets/img/architecture-overview.png"/>
</center>

*Process Engine & Infrastructure*

*   [Process Engine](#process-engine): The process engine is a java library responsible for executing BPMN 2.0 processes and workflows. It has a lightweight POJO core and uses a relational database for persistence. ORM mapping is provided by the mybatis mapping framework.
*   [Spring Framework Integration](#spring-framework-integration)
*   [CDI / Java EE Integration](#cdi-and-java-ee-integration)
*   [Runtime Container Integration](#runtime-container-integration) (Integration with application server infrastructure.)

*Web Applications*

*   [REST API](ref:/api-references/rest/) The REST Api allows using the process engine from a remote application or a Java Script application. (Note: The documentation of the REST Api is factored out into an own document.)
*   [camunda Tasklist](#tasklist) A web application for human workflow management and user tasks. The tasklist allows process participants to inspect their workflow tasks and navigate to task forms in order to work on the tasks and provide data input.
*   [camunda Cockpit](#cockpit) A web application for process monitoring and operations. camunda Cockpit allows to search for process instanced, inspect their state and repair broken instances.
*   [camunda Cycle](#cycle) A webapplication for synchronizing BPMN 2.0 process models between different modeling tools and modelers.

*Additional Tools*

*   [camunda Modeler](#modeler): eclipse plugin for process modeling.
*   [camunda-bpmn.js](https://github.com/camunda/camunda-bpmn.js): javascript framework for parsing, rendering and executing BPMN 2.0 from XML source.