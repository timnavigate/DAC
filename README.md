## DAC
`Docs as Code` proof of concept and check of goals:
* versioning, reusability, automation, blah-blah-blah
* llm-agents prepared preparation level
* who reads this and how

### BOKs
[content](boks/README.md)

### Playgrounds
* [ascidoc](playgrounds/asciidoc/README.md)
* [d2](playgrounds/d2/README.md)
* [drawio](playgrounds/drawio/README.md)
* [openapi/asyncapi](playgrounds/openapi-vs-asyncapi/README.md)
* [zenuml](playgrounds/zenuml/README.md)
* [mermaid](playgrounds/mermaid.md)

### Official Docs
- [UML 2.5](https://www.uml-diagrams.org/)
- [BPMN 2.0](https://www.bpmn.org/)
  - [DES](https://habr.com/ru/articles/1042754/) - Discrete Event Simulation, Дискретно-событийное (имитационное) моделирование
- [C4model](https://c4model.com/diagrams/notation)
  - Static structure diagrams
    - [System context diagram](#system-context-diagram)
    - [Container diagram](#container-diagram)
    - [Component diagram](#component-diagram)
    - Code diagram
  - Supporting diagrams
    - [System landscape diagram](#system-landscape-diagram)
    - [Dynamic diagram](#dynamic-diagram)
    - Deployment diagram

### Github auto-previews checklist
- [x] `.md` by default
- [x] `.adoc` by default
- [x] `.png` by default
- [x] `.svg` by default
- [x] `.html` by default
- [x] `.pdf` by default
- [x] `.jpg` by default pasted via `![_title_](_url_)`
- [ ] `.mermaid` by default
- [ ] ...

### Diagrams as code tools
* [PlantUML](https://plantuml.com) - diagram types
* [ZenUML](https://zenuml.com)
* [D2](https://d2lang.com)
* [Mermaid](https://mermaid.js.org) - web-based diagramming
* [Graphviz](https://graphviz.org) - network diagrams
* [Structurizr](https://structurizr.com) - ADR documentation and communication based on C4 Modeling
* [WebSequenceDiagrams](https://websequencediagrams.com)
* [SequenceDiagram](https://sequencediagram.org)
* [drawio](https://drawio.com) - Web-based DaC
* [Holori](https://app.holori.com) - terraform code to diagrams
* [Diagrams Mingrammer](https://diagrams.mingrammer.com) - Cloud System Arch DaC
* [CloudSkew](https://app.cloudskew.com) - cloud arch diagramming
* [BMPN](https://bpmn.io)
* [IcePanel](https://icepanel.com)
* [Lucidchart](https://lucidchart.com) - collaborating diagramming
* [Excalidraw](https://excalidraw.com) - collaborating whiteboarding
* [Holst](https://holst.so/) - collaborating whiteboarding
* [tldraw](https://tldraw.com) - collaborating sketching
* [Gliffy](https://gliffy.com) - collaborating drag-and-drop

### C4
#### System context diagram
A system context diagram is a good starting point for diagramming and documenting a software system, allowing you to step back and see the big picture. Draw a diagram showing your system as a box in the centre, surrounded by its users and the other systems that it interacts with.

Detail isn’t important here as this is your zoomed out view showing a big picture of the system landscape. The focus should be on people (actors, roles, personas, etc) and software systems rather than technologies, protocols and other low-level details. It’s the sort of diagram that you could show to non-technical people.
##### Scope
A single software system.
##### Example
<img width="1710" height="1415" alt="image" src="https://github.com/user-attachments/assets/d1f0038f-3746-43ef-b979-5f92e38543c3" />

##### Primary elements
The software system in scope.
##### Supporting elements
People (e.g. users, actors, roles, or personas) and software systems (external dependencies) that are directly connected to the software system in scope. Typically these other software systems sit outside the scope or boundary of your own software system, and you don’t have responsibility or ownership of them.
##### Intended audience
Everybody, both technical and non-technical people, inside and outside the software development team.
##### Recommendation
Recommended? Yes, a system context diagram is recommended for all software development teams.
#### Container diagram
Once you understand how your system fits in to the overall IT environment, a useful next step is to zoom in to the system boundary with a container diagram. In C4, a container is an application or a data store. For example, a server-side web application, a client-side single-page application, a desktop application, a mobile app, a database schema, a folder on a file system, an Amazon Web Services S3 bucket, etc.

The container diagram shows the high-level shape of the software architecture and how responsibilities are distributed across it. It also shows the major technology choices and how the containers communicate with one another. It’s a simple, high-level technology focussed diagram that is useful for software developers and support/operations staff alike.
##### Scope
A single software system.
##### Example
<img width="2471" height="2339" alt="image" src="https://github.com/user-attachments/assets/b7bc22d5-c4aa-4725-9454-78d4d43a0f9d" />

##### Primary elements
Containers within the software system in scope.
##### Supporting elements
People and software systems directly connected to the containers.
##### Intended audience
Technical people inside and outside the software development team; including software architects, developers and operations/support staff.
##### Recommendation
Recommended? Yes, a container diagram is recommended for all software development teams.
##### Notes
This diagram says very little about deployment aspects such as clustering, load balancers, replication, failover, etc because it will likely vary across different environments (e.g. production, staging, development, etc). Deployment information is better captured via one or more `deployment diagrams`, one per environment.
#### Component diagram
Next you can zoom in and decompose a container to describe the components that reside inside it; including their responsibilities and the technology/implementation details.
##### Scope
A single container.
##### Example
<img width="3695" height="2590" alt="image" src="https://github.com/user-attachments/assets/d1a303f6-769e-4a95-bd6a-2a6a6a5e2cbf" />

##### Primary elements
Components within the container in scope.
##### Supporting elements
Containers (within the software system in scope) plus people and software systems directly connected to the components.
##### Intended audience
Software architects and developers.
##### Recommendation
Recommended? No, only create component diagrams if you feel they add value, and consider automating their creation for long-lived documentation.
#### Dynamic diagram
A dynamic diagram can be useful when you want to show how elements in the static model collaborate at runtime to implement a user story, use case, feature, etc. This dynamic diagram is based upon a `UML communication diagram` (previously known as a “UML collaboration diagram”). It is similar to a `UML sequence diagram` although it allows a free-form arrangement of diagram elements with numbered interactions to indicate ordering.
##### Scope
A particular feature, story, use case, etc.
##### Example (collaboration style)
<img width="3015" height="1594" alt="image" src="https://github.com/user-attachments/assets/1e265869-16a8-401a-9507-85183c4a276a" />

##### Example (sequence style)
<img width="2450" height="825" alt="image" src="https://github.com/user-attachments/assets/475b40f5-740d-4177-8489-efa10a8a883b" />

##### Primary and supporting elements
Your choice - you can show software systems, containers, or components interacting at runtime.
##### Intended audience
Technical and non-technical people, inside and outside the software development team.
##### Recommendation
Recommended? No, dynamic diagrams should be used sparingly to show interesting/recurring patterns or features that require a complicated set of interactions.
##### Notes
The collaboration and sequence styles show the same information in a different way, so feel free to use whichever you prefer.

#### System landscape diagram
The system context, container, component, and code diagrams are designed to provide a static view of a single software system but, in the real-world, software systems never live in isolation. For this reason, and particularly if you are responsible for a collection/portfolio of software systems, it’s often useful to understand how all of these software systems fit together within a given enterprise, organisation, department, etc. Essentially this is a map of the software systems within the chosen scope, with a set of system context, container, component, and code diagrams for each software system of interest.

From a practical perspective, a system landscape diagram is really just a system context diagram without a specific focus on a particular software system.
##### Scope
An enterprise/organisation/department/etc.
##### Example
<img width="3260" height="2098" alt="image" src="https://github.com/user-attachments/assets/2e0c1b6d-1053-4b62-a12d-9eb8ed841dfa" />

##### Primary elements
People and software systems related to the chosen scope.
##### Intended audience
Technical and non-technical people, inside and outside the software development team.
##### Recommended?
Yes, particularly for larger organisations - it’s a bridge into the enterprise architecture world.

