---
layout: post
title: "Explainability in AI"
date: 2019-06-12
categories: blog
---

In this post, I will share a few of my thoughts on explainability in AI/ML.

## Motivating Stories

These situations ought to explain why explainability in AI is important.
 - When a human is riding a self-driving taxi, and the taxi takes a sudden unexpected detour, you become suspicious and probably scared, wondering if the car is malfunctioning or has it been hacked and are you being taken to a different place. The AI agent driving the taxi will need to give an explanation — something like, the road ahead has been blocked, or there is some demonstration on the street ahead, etc.. and then go on to say how the detour will help them reach the destination. This is also often the behavior we would expect from a human taxi driver.
 - Suppose a bank has a machine learning model that determines the creditworthiness of a person based on which they give out loans to their customers. The model will predict whether he will default on his payments. In such a scenario, if a customer is denied a loan because his score is too low, the bank should at least be in a position to explain why they are denying him the loan and maybe ways by which he can improve his score.
 - In applications like content recommendation, when we are recommended new content, we would like to know what made the machine learning model suggest that particular content to us. An opaque recommendation system might raise privacy concerns on whether our web activity is being tracked by the content provider. A brief explanation such as “You are being recommended X video because you have previously watched and liked Y video” will make the experience far less creepy.
 - In an application that detects cat pictures, can the model explain why a particular image was classified as a cat? For instance, can it describe the characteristics of a cat-like having a tail, fluffy fur, pointy ears, eyes, etc.? We would expect a human who would recognize a cat picture to do this; should our machines also do something similar?

## Criticisms

In the face of the above motivations, there are the following criticisms of the concept -
 - The importance of explainability is overblown; the performance of a model is more important ( <a href="https://news.ycombinator.com/item?id=18766485" target="_blank">Geoff Hinton Dismissed the Need for Explainable AI</a> ). Focusing and insisting that models have to be explainable might slow down ML adoption.
 - There are plenty of use cases like OCR or image classification, where algorithms have been perfected, and the risk of a false positive classification is low, so we do not need to know how the model arrived at a result as long as the results are accurate. I would rather be diagnosed by a robot doctor that is 90% accurate and gives no explanation than by one that is 80% accurate with explanations( This is a quote from one of Pedro Domingos’s articles. The article and my reply to this criticism are <a href="https://anirudhacharya.medium.com/not-necessarily-d1a2ea013877" target="_blank">here</a>).
 - We already have model agnostic tools to interpret the results of machine learning models, like partial dependence plots, Local Interpretable Model-agnostic Explanations( <a href="https://www.oreilly.com/content/introduction-to-local-interpretable-model-agnostic-explanations-lime/" target="_blank">LIME</a>), ascertaining feature importance, or detect biases and problems in data used for training.
 - As long as the problem definition was completely captured by the loss function and the data collection happens in a controlled setting and data biases are accounted for while training, then explaining the results of the model is unnecessary.

I believe most of these criticisms are weak and can be easily countered. But the real questions that need answering are the following.

## Open Questions

- I am usually of the belief that an appropriate formulation of the problem is often half the solution. Explainability in ML is not properly defined. What does it mean for an ML model to be explainable, and how is it different from Causal Machine Learning? An explanation often reduces to establishing some causality for the obtained results. Are there any explanations that are not causal?
- We need to distinguish and tease apart seemingly related concepts such as interpretability of ML models, explainability in ML models, and causality in ML/AI/statistics(à la Judea Pearl’s book “<a href="https://www.amazon.com/dp/B075CR9QBJ/ref=dp-kindle-redirect" target="_blank">The Book of Why</a>”).
- Should we be looking for some theory of explainable models or just try to address the problem on a case-by-case basis? When is explainability desirable?