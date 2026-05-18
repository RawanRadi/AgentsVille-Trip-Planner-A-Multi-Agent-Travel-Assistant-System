# AgentsVille Trip Planner: Multi-Stage AI Travel Assistant

An intelligent, multi-stage agentic system designed to build and refine custom travel itineraries for the fictional city of AgentsVille. This project demonstrates how to move beyond static LLM text generations by constructing an engine capable of structured JSON planning, logical reasoning, and state-reflective tool execution.

The application leverages a two-part architectural approach inside a Jupyter Notebook environment to handle user constraints, budget caps, and dynamic schedule updates.

## 🗺️ System Architecture

The AI Trip Planner functions via two decoupled operational phases:

### Phase 1: The Expert Planner (Structured Generation)
* **Objective:** Transforms raw user input (duration, destination, budget, specific interests) into a coherent, daily travel itinerary.
* **Mechanism:** Utilizing advanced prompt engineering and schema constraints, the LLM is forced to reason through a structured planning loop.
* **Output:** Generates a robust, production-ready JSON object strictly validated against a predefined **Pydantic model** to guarantee schema safety for downstream modules.

### Phase 2: The Resourceful Assistant (Tool-Augmented ReAct Agent)
* **Objective:** Handles fluid conversational adjustments, ad-hoc user modifications, and verification tasks on the baseline itinerary.
* **Mechanism:** Implements a classic **ReAct (Reasoning and Acting)** loop framework. The agent handles changes by moving through a programmatic state lifecycle:
  * 🧠 **THINK:** Analyzes the modification request against the current schedule context and plans an action.
  * ⚙️ **ACT:** Formulates a structured API call payload to execute an internal tool (e.g., calling a simulated Activities API).
  * 👁️ **OBSERVE:** Consumes the tool's runtime data execution feedback to update its internal environment knowledge.
* **Output:** Merges new constraints seamlessly into the final, optimized itinerary.

## 🛠️ Core Engineering Features
* **Structured Output Enforcement:** Structural validation using Pydantic models to ensure reliable machine-readable data structures.
* **Custom ReAct Loop Execution:** From-scratch simulation of the Agentic ReAct paradigm (Thinking ➔ Acting ➔ Observing).
* **Deterministic API Tooling:** Local Python functions mimicking external service integrations and catalog search endpoints.
