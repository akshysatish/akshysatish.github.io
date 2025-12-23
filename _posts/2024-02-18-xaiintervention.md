---
title: "Explainable AI: Intervention Designs"
excerpt_separator: "<!--more-->"
categories:
  - Blog
tags:
  - Post Formats
  - readability
  - standard
---

The following post is an analysis of the paper **Selective Explanations: Leveraging Human Input to Align Explainable AI** by **Vivian Lai et al.**

## What is Explainable AI?
Explainable AI (XAI) is a field focused on making complex AI systems, especially "black box" models like deep learning, understandable to humans by revealing why they make certain decisions, fostering trust, debugging, ensuring fairness, and meeting regulations (like GDPR). It uses various methods (like LIME, SHAP) to show which data features influenced an AI's output, allowing users to verify, trust, and govern these systems in critical areas like healthcare, finance, and autonomous vehicles. 

## Current Landscape
Recent years have seen a vast collection of XAI algorithms but they have significant gaps in how humans produce and consume explanations. Empirical human-subject studies have not found conclusive evidence that they help end-users. AI explanations are often unintuitive and demand significant effort for people to process and understand. Current XAI paradigms deal only with the reasoning process and concern little with the communication process

## AI explanations: Mixed results?
### Positives:
- Improves people’s understanding of the model
- Enhance people’s subjective perception of AI
- Help data scientists debug the model

### Negatives:
- End users found the explanations hard to use
- Time consuming
- Cognitively demanding

> These negatives resulted in lower task satisfaction!!

## The Human Element...
Social sciences literature point out that the lack of compatibility with how humans use explanations is the main drawback in current XAI.

> **Malle's Theory of Explanation**
>
>A human explainer must engage in two fundamental processes to produce explanations
> - Gather all reasons that can explain 
> - Communicate the explanation in social interactions

When communicating explanations, people rarely present all explanatory causes. Instead, they **select** what they believe as serving the recipient’s interest for achieving their goal, such as finding common grounds and providing new knowledge.

Selectivity is a fundamental property of human explanations. 
The goal is to selectively present a subset of model reasonings based on what aligns with the recipient’s preferences

## The Pitfall
A prominent XAI pitfall is the increasing overreliance when the AI is wrong, which is especially problematic in the common use case of XAI for decision support

**EXPECTATIONS..**

Explanations can help people detect flawed model reasoning and make better decisions

**REALITY..**

Failed to observe this effect  
(or)  
Found that explanations make people more likely to blindly follow the model
when it is wrong compared to showing only AI predictions

## Framework: Selective Explanation with Human Input
- **Input step:** collecting input from humans on a small sample that can be used to infer beliefs about the user
- **Selection step:** generating selective explanations according to beliefs about the recipient’s preferences for explanation, as inferred from the input collected in step 1

This framework accounts for different selectivity goals, types of input, etc and reduces over-reliance on AI, improves collaborative decision making, and subjective perceptions of AI systems

> Framework is contingent on the goal of selectivity which can vary with different use cases. We may have to make different design choices in where and how we get the input and how we present the explanations.

![frmwrk](/assets/images/frmwrk.png "Framework")

### Selectivity Goal
- **Relevance:** 
Prioritize reasons that the recipient would deem relevant or important to the task
- **Abnormality:**
Prioritize reasons that the recipient would find abnormal or surprising
- **Changeability:**
Prioritize reasons that can be changed or are more easily changeable

## Design Choices for framework
### Who gives the input?
Straightforward solution: Get it from the individual recipient of the explanations. But
- Additional workload
- Requires time and resources of the individual

**Assumption:** People often share the same preferences for a task.

**Alternative solution:** Get it from a panel of annotators similar to the target users

Also, what if most individuals cannot tell what is relevant or abnormal and lack domain knowledge?

Domain experts can provide input to improve the experience for all users.

### Input elicitation method
**Yay!! We got the input.** But now the elicitation method asks the input provider

"Which features should be considered as relevant/abnormal/changeable for this use case?"

People are often better at articulating their knowledge or opinions with examples. So, we can ask the above question using a small sample of examples as follows:
- Open-ended: ask directly to pick features from the example
- Critique-based: ask for agreement or disagreement with AI explanations for the given example

### How to present selective explanation
This decision depends on UI characteristics. Some possibilities are:
- For text/image data: saliency map to visually highlight important keywords or superpixels
- For tabular data: horizontal bar chart to visualize the importance of different features in the given instance

**Present misaligned features or hide it?**

Only presenting features that align with the predicted recipient preferences can be lightweight visually but comes with the tradeoff of faithfulness
So, perhaps keep the misaligned features but augment them with different visual cues.

## Study
The above mentioned paper studies the effect of the framework as an intervention design in the context of AI-supported sentiment judgment in a movie sentiment prediction task. They found the following:
- Selective explanations improve users' perceived understanding of the model by reducing noise and focusing on relevant information.
- Selective explanations with random sampling improved participants' decision-making and reduced their overreliance on the model.
- Gathering input from domain experts could further enhance the benefits of selective explanations.
- Giving users control over explanations through self-input can improve their perception of the AI's usefulness and task efficiency, but at the cost of increased workload.

## Related Reading
- Fel et al. Harmonizing the object recognition strategies of deep neural networks with humans. NeurIPS'22
- Nguyen et al. Visual correspondence-based explanations improve AI robustness and human-AI team accuracy. NeurIPS'22
- Zhang and Lim. Towards Relatable Explainable AI with the Perceptual Process. CHI'22
- Wang et al. Designing Theory-Driven User-Centric Explainable AI. CHI'19
- Ehsan et al. Expanding Explainability: Towards Social Transparency in AI systems. CHI'21
