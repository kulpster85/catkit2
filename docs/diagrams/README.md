# Architecture diagrams

This directory contains PlantUML diagrams that document the architecture of
catkit2, generated from the source code in `catkit2/` (Python) and
`catkit_core/` (C++).

## Diagrams

| File | Type | Contents |
|---|---|---|
| `architecture_overview.puml` | Component | High-level overview: testbed server, service processes, experiment process, shared memory and logging/tracing flows. |
| `python_classes.puml` | Class | Python classes: `Service`, `ServiceProxy`, `TestbedProxy`, `Testbed`, `Experiment`, base services (camera, DM), device proxies, simulator and logging helpers. |
| `cpp_core_classes.puml` | Class | C++ `catkit_core` classes: `Service`, `ServiceProxy`, `TestbedProxy`, `Server`/`Client`, `DataStream`/`Tensor`, `Shareable`/memory hierarchy, `Event`, message broker, logging and tracing. |
| `sequence_service_startup.puml` | Sequence | How a service is started by the testbed, registers itself and transitions through its lifecycle states. |
| `sequence_command_property.puml` | Sequence | How property get/set and command execution requests travel from a `ServiceProxy` through ZeroMQ to the service handlers. |
| `sequence_datastream.puml` | Sequence | How frames are submitted to and read from a `DataStream` through shared memory and events. |
| `sequence_experiment.puml` | Sequence | The `Experiment.run()` lifecycle, including output path creation, logging setup and the pre/main/post experiment hooks. |

## Rendering

Render a diagram to PNG or SVG with [PlantUML](https://plantuml.com/):

```
plantuml docs/diagrams/python_classes.puml
plantuml -tsvg docs/diagrams/*.puml
```

Alternatively, paste the file contents into the
[PlantUML web server](https://www.plantuml.com/plantuml/) or use an IDE
plugin (e.g. the PlantUML extensions for VS Code or PyCharm).

## Keeping the diagrams up to date

These diagrams are maintained by hand and reflect the source code at the time
of writing. When changing public interfaces of the classes shown here (for
example `Service`, `ServiceProxy`, `DataStream` or `Experiment`), please
update the corresponding diagram. The source code remains the authoritative
reference.
