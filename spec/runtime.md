# Runtime Environment

## Distributing Agents

Agents should be distributed as OCI container images.

## Running Agents

Tools should execute agents in a runtime environment compatible with the OCI runtime specification.
Tools must set the following environment variables when executing the agent process:

```sh
# The base URL under which the HTTP interface is served by the tool
MINION_API_BASE_URL
# A token that agents can use to authorize themselves against the HTTP interface
MINION_API_TOKEN
```

## Nested Containers

Agents often need to themselves run containers to perform their task.
In particular, one viable strategy is for the agent to spawn [development containers](https://containers.dev/).

To support this behavior, tools should support running nested container workloads.

> [!TIP]
> This can be achieved with containerization (e.g. using [sysbox](https://github.com/nestybox/sysbox)) or with virtualization.

> [!WARNING]
> At the moment, the spec lacks a way for packaged agents to communicate this requirement.
> Possible future solutions include using OCI labels, OCI annotations or a separate agent manifest file bundled in a fixed location in the container image.
