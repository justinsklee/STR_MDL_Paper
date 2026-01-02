# Appendix A. Prompt Templates for Corrective Learning Experiments

This document provides the **verbatim prompt templates** used in the corrective learning
experiments described in the accompanying paper, "Developing custom structural model review and editing modules 
through corrective learning-based conversational programming"
The prompts are preserved exactly to support **reproducibility, transparency, and reuse**.

---

## A.1 Prompt for Try Again Method

```text
"{task_description}

Previous response:
{previous_response}

The Python code is wrong. Try again."
```

---

## A.2 Prompt for LLM Corrective Learning Method

```text
Your previous attempt(s) failed to produce correct output.
Please analyze what went wrong and provide corrected code.

CURRENT TASK:
{task_description}

{previous_attempts_text}

Please provide:
1. SELF-ANALYSIS:
   Concisely explain (max 400 characters) what went wrong in the previous attempt and why it failed.
   The assessment you provide will be saved and re-used for future tasks, so provide assessment that
   is NOT about any specific floors, grids, or elevations (e.g. third floor). This will allow your
   assessment to be generalized for future tasks that are similar to this task.

2. CORRECTED CODE:
   Provide new Python code that addresses these issues.

Focus on the specific failure and ensure your corrected code addresses the root cause.
```

---

## A.3 Prompt for LLM-driven Soft-Match Corrective Instruction Query Method

```text
You are helping to match user queries with relevant corrective instruction entries.
User Query: "{user_input}"
Available Entries:
{entries_text}

Please analyze the user query and identify which entries are most relevant. Consider:
- Semantic similarity between the query and keywords/instruction content
- Related concepts that might not be exact keyword matches
- Context and intent behind the user's query

Return your response as a JSON array containing only the entry numbers (1-based) that are relevant,
ordered by relevance (most relevant first). If no entries are relevant, return an empty array.

Example format: [3, 7, 1] or []
Only return the JSON array, no other text.
```

---

## Notes on Usage

- All prompts are provided **verbatim** as used in the experiments.
- This file serves as an archival artifact for peer review and replication.
