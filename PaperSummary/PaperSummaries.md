# [ChatDev - Communicative Agents for Software Development](https://arxiv.org/abs/2307.07924)

- Splitting a large task in smaller quantitative tasks performed by multiple agents to achieve better results
- Asking a LLM to self-reflect till it converges on a single answer
- Swapping roles and asking the opposite on providing feedback, and then swapping back can increase performance in certain situations.
- Providing LLM with tools which it can use to self-reflect


# [Reflexion Language Agents with Verbal Reinforcement Learning](https://arxiv.org/abs/2303.11366)

- Asking model on failure how it could improve itself, then summarizing that and using in memory and prompting again.
- Keeping a short detailed memory of the actions that have just happened, and a summarized long term memory for past experiences.
- Use LLM to generate self-reflection, and then storing them in a vector DB, pulling them with RAG for long-term memory


# [Cognitive Architectures for Language Agents](https://arxiv.org/abs/2309.02427)

- Short term and long term memory. Short term includes the imitate actions state, Long term memory is divided into three distinct types. Procedural memory stores the production system itself: the set of rules that can be applied to working memory to determine the agent’s behavior. Semantic memory stores facts about the world, while episodic memory stores sequences of the agent’s past behaviors.
- Using augmented retrieval to load the most relevant memory
- model can choose between retrieval (read from long-term memory), reasoning (update the short-term working memory with LLM), and learning (write to long-term memory)


# [AutoGen Enabling Next-Gen LLM Applications via Multi-Agent Conversation](https://arxiv.org/abs/2308.08155)

- AutiGen agent capabilities are powered by LLM backed agents, human proxy agents, and tool backed agents.
- AutoGen utilizes conversation programming, a paradigm that considers two concepts: computation: the actions agents take to compute their response in a multi-agent conversation. And the second is control flow: the sequence (or conditions) under which these computations happen.
- Autogen uses various control flow management patterns: 1) Natural language control via LLM, 2) programming language control, 3) Control transition between natural and programming language. 


# [MetaGPT Meta Programming for A Multi-Agent Collaborative Framework](https://arxiv.org/abs/2308.00352)

- The framework follows Standardized Operating Procedures (SOPs) that guide the sequence of operations. 
- Structured Communication Interfaces: Agents communicate through documents and diagrams (structured outputs) rather than dialogue. These documents contain all necessary information, preventing irrelevant or missing content. Subscribe Mechanism: information is stored in a global message pool. Any agent can directly retrieve required information from the shared pool, eliminating the need to inquire about other agents and await their responses. Instead of relying on dialogue, agents utilize role-specific interests to extract relevant information. They can select information to follow based on their role profiles. In practical implementations, an agent activates its action only after receiving all its prerequisite dependencies.


# [AgentBoard An Analytical Evaluation Board of Multi-turn LLM Agents](https://arxiv.org/abs/2401.13178)

- AgentBoard introduces a unified progress rate metric, in addition to success rates, to track detailed advancements of agents. This metric helps in identifying significant progress that might not be evident through success rates alone.
- AgentBoard assess LLMs across several facets: memory that measures incorporating long-range information in context, planning that assesses decomposing complex goals into manageable sub-goals, world modeling which tests knowledge necessary for task completion, retrospection that captures the ability to use environmental feedback, grounding that focuses on competency in generating valid actions, and spatial navigation that represents efficiency in moving to a target location


# [ReAct Synergizing Reasoning and Acting in Language Models](https://arxiv.org/abs/2210.03629)

-


# [Gorilla Large Language Model Connected with Massive APIs](https://arxiv.org/abs/2305.15334)

-


# [Chain-of-Thought Prompting Elicits Reasoning in Large Language Models](https://arxiv.org/abs/2201.11903)

- A chain of thought is a series of intermediate natural language reasoning steps that lead to the final output
- COT allows models to decompose multi-step problems into intermediate steps, which means that additional computation can be allocated to problems that require more reasoning steps.
- COT provides an interpretable window into the behavior of the model, suggesting how it might have arrived at a particular answer and providing opportunities to debug where the reasoning path went wrong.
- COT reasoning can be used for tasks such as math word problems, commonsense reasoning, and symbolic manipulation, and is potentially applicable to any task that humans can solve via language.

# [Understanding the planning of LLM agents A survey](https://arxiv.org/abs/2402.02716)

- They present a novel and systematic taxonomy for LLM-based agent planning that divides existing works into five important categories, covering task decomposition, multi-plan selection, external module-aided planning, reflection and refinement and memory-augmented planning

- Task Decomposition: This kind of method adopts the idea of divide and conquer, decomposing the complicated into several sub-tasks and then sequentially planning for each sub-task.
  - Task decomposition generally involves two crucial steps: firstly, decomposing the complex task, referred to as the “decompose” step, and secondly, planning for the sub-tasks, known as the “sub-plan step”. 
  - Decomposition-first methods decompose the task into sub- goals first and then plan for each sub-goal successively
  - Interleaved decomposition involves interleaved task decomposition and sub-task planning, where each decomposition only reveals one or two sub-tasks at the current state

- Multi-plan Selection. This kind of method focuses on lead- ing the LLM to “think” more, generating various alternative plans for a task. Then a task-related search algorithm is em- ployed to select one plan to execute.
  - Multi-plan generation involves generating a dozen paths of plans to comprise the candidate plan set. Mainstream methods consider employing uncertainty in the decoding process of generative models.
  - Self-consistency applies the naive majority vote strategy, regarding the plan with the most votes as the optimal choice. Tree-of-Thought (ToT) supports tree search algorithms, such as conventional BFS and DFS. When selecting a node for expansion, it uses LLM to evaluate multiple actions and chooses the optimal one. LLMMCTS and RAP also employ the Monte Carlo Tree Search (MCTS) algorithm for search. LLM A* utilizes the classic A* algorithm from artificial intelligence to assist LLM in search. The Chebyshev distance from the current position to the target position serves as the heuristic cost function for selecting the optimal path.

- External Planner-Aided Planning. This methodology is crafted to employ an external planner to elevate the planning procedure, aiming to address the issues of efficiency and in- feasibility of generated plans, while the LLM mainly plays the role in formalizing the tasks. 

- Reflection and Refinement. This methodology emphasizes improving planning ability through reflection and refinement. It encourages LLM to reflect on failures and then refine the plan.
    - Due to existing hallucination issues and insufficient reasoning abilities for complex problems, LLM-Agents may make errors and get stuck in “thought loops” during planning due to limited feedback. Reflecting on and summarizing failures helps agents correct errors and break out of such loops in subsequent attempts. 

- Memory-augmented Planning. This kind of approach enhances planning with an extra memory module, in which valuable information is stored, such as commonsense knowledge, past experiences, domain-specific knowledge, et al. The information is retrieved when planning, serving as auxiliary signals.
  - In contrast to deep reinforcement learning where updates are achieved by modifying model parameters, in the LLM agent, this update occurs through self- reflection by the LLM itself, culminating in textual verbal feedbacks. These textual feedbacks can serve as both long- term and short-term memory, influencing the agent’s subsequent planning outputs through the prompts.
  - Generative Agents store the daily experiences of human-like agents in text form and retrieve memories based on a composite score of recency and relevance to the current situation. MemoryBank, TiM, and RecMind encode each memory using a text encoding model into a vector and establish an indexing structure, such as FAISS library. During retrieval, the description of the current status is used as a query to retrieve memories from the memory pool.
  - Embodied memory involves fine tuning the LLM with the agent’s historical experiential samples, embedding memories into the model parameters.

- Interactive Retrieval Environments: Interactive retrieval environments simulate the process of information retrieval and reasoning that humans undergo in real life. In these environments, agents are often allowed to interact with search engines and other web services, using actions such as searching keywords or executing click, forward, and backward operations to acquire more information, thereby obtaining answers to questions or completing information retrieval tasks.

- Interactive Programming Environments: Interactive programming environments simulate the interaction between programmers and computers, testing the agent’s planning ability in solving computer-related problems. In these environments, agents are required to interact with computers to solve problems by writing code or instructions. They would receive various feedback including compile and runtime error messages, as well as execution results.