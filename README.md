# AgentArpanet visualization

An interactive isometric view of two lab machines (rtx-01 and v100-01) on an AgentArpanet network. It shows the hub, the WireGuard tunnel, and each node's parts: node-agent, the dashboard, the tailscale sidecar, the model and the collections. A walkthrough follows one question step by step:
1. On rtx-01's host, its owner asks their agent in opencode.
2. opencode's model searches rtx-01's notes and finds the labs it can reach, through node-agent's MCP server.
3. It asks v100-01's agent with `ask_peer`.
4. v100-01's agent answers from the one collection rtx-01 may read.

It matches AgentArpanet v0.5:
- **The owner's agent is opencode**, running on the node's own model. It reaches the node through the MCP server on `127.0.0.1:8091`.
- **Admin happens only in the dashboard** (`127.0.0.1:8092`) or with `./agentnet`.
- **Other nodes only ever talk to a node's agent.**

Open `index.html` in a browser, or view the GitHub Pages site. It's a single static page, and loads three.js r128 from jsDelivr.

The two `netmap-*.json` files are illustrative netmaps, linked from step 1 of the walkthrough.
