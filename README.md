# Shambhavi-langgraph-MAT496
### Setup:
Followed the instructions in the README to create an environment and install dependencies.
## Module 1 
### Lesson 1-Motivation:
- Many LLM applications use control flow which forms a chain which is very reliable because they use same control flow every time.
- Agent is a control flow determined by an LLM  
- When we go from a simple agent (router) to complex (autonomous) the application reliability decreases and the level of control increases.
![Alt text](image1.png)
- We can balance reliability with langgraph
- Langgraph has persistance, streaming, human-in-the-loop and controllability.
- Langgraph comes with an IDE which helps you visualise and debug the agents that you build.
- Towards the end of the video, modules and their overview has been discussed.

### Lesson 2-Simple Graph:
- We build a simple graph with 3 nodes and one conditional edge.
- State is an object that we pass between the nodes and edges of the graph
- Edges connect the nodes
- We use if statement to execute the conditional state between node 2 and 3 by defining 50-50 probablity of both.
- When **invoke** is called, graph starts execution from START node and the conditional node will traverse from node 1 to node 2 or 3 using the 50/50 decision rule.
**Tweaking**: I used the same logic as explained in the video to make a graph corresponding to the problem statement-How much CGPA did I get.
![Alt text](image2.png)

### Lesson 3- Langsmith Studio
- Explains how to setup langsmith studio for viewing and testing agents.
- To track the various runs of graphs we use thread section of the studio.
- Multiple inputs can be added in graph state to add nodes and form a graph.
![Alt text](image3.png)

### Lesson 4- Chain:
- We build a simple chain that uses chat messages in our graph, uses chat models, binds tools to our LLM and executes tool calls in our graph.
- We can take a list of messages and pass it onto the chat model
- To connect our chat model to external tool like an API it requires a particular payload to run.
- To append a message use reducers.
- **Tweaking**: Made changes in the notebook, changed the datasets and tools to produce the corresponding graph.

### Lesson 5- Router:
- Router is a simple kind of agent which routes between response and tool calling 
- Conditional edge is going to look at the output and if that output is a tool call it will route to the tools node, otherwise it will just end.
![Alt text](image4.png)
- **Tweaking**: Changed the tool from multiplication to subtraction and changed the datasets.
![Alt text](image5.png)

### Lesson 6- Agent:
- We can turn router into a generic agent architecture.
- The model can either end or can pass the tool output back to he model.
- In the video they showed three sequential tool calls made by the agent.
- You can see the tracing of your project in langsmith, where it shows the various steps and process of your project. You can also check latency and token count.
**Tweaking**:
![Alt text](image6.png)

### Lesson 7- Agent with memory:
- Introduced memory in our agent 
- State is transient to single graph execution
- Graph- Control flow of nodes, edges.
- Each sequential node is a superstep whereas parallel nodes have common superstep
- Checkpoints contain the state of the graph at each step of the execution.
- Thread is a collection of checkpoints
- NLM is turned into a tool call which is passed to the tools node which provides the output and it goes back to the assistant in order to produce the output in Natural Language.
**Tweaking**:
![Alt text](image6.png)





 