# AgentArpanet visualization

An interactive isometric view of two lab machines (Stanford-01 and Storey) on an AgentArpanet network. It shows the hub, the WireGuard tunnel, and each node's parts: node-agent, the dashboard, the tailscale sidecar, the model and the collections. A walkthrough follows one question step by step:
1. On Stanford-01's host, its owner asks their agent in opencode.
2. opencode's model searches Stanford-01's notes and finds the labs it can reach, through node-agent's MCP server.
3. It asks Storey's agent with `ask_peer`, which sends an A2A task to Storey.
4. Storey's agent answers from the one collection Stanford-01 may read.

It matches AgentArpanet v0.6:
- **Every node runs its own opencode instance**, drawn as a screen in front of each machine. That's how each lab's people use the network: Stanford-01's owner asks Stanford-01's opencode, and labs reach each other only through their nodes' agents.
- **The owner's agent is opencode**, running on the node's own model. It reaches the node through the MCP server on `127.0.0.1:8091`.
- **Admin happens only in the dashboard** (`127.0.0.1:8092`) or with `./agentnet`.
- **Nodes talk [A2A 1.0](https://a2a-protocol.org)** (JSON-RPC at `:9000/a2a`), and nothing else. Stanford-01 reads Storey's extended Agent Card, then asks as a streamed task; the answer is the task's artifact.
- **Other nodes only ever talk to a node's agent.**

Open `index.html` in a browser, or view the GitHub Pages site. It's a single static page, and loads three.js r128 from jsDelivr.

The two `netmap-*.json` files are illustrative netmaps, linked from step 1 of the walkthrough.
