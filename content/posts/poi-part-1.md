---
title: "Relevant vs. Irrelevant: Building the World's Most Expensive Binary Classifier"
date: 2025-01-01
draft: False
math: True
---

> You are being watched.......

I've been putting off the first post on my blog for a while now. Struggling to find a good topic to start with that was "cool enough to write" and "geeky enough to care". Then I was re-watching Person of Interest  (PoI).

As an MLE, re-watching this show is a trip. It's one of the few media pieces that respect some technical complexity of AI and I thought why not imagine what it would be like to design a production-ready system design for "The Machine" in this era of LLMs and almost-AGIs.

## The Premise

Now if you are unfamiliar with the show, here's a quick pitch...

### The Show

*Person of Interest* follows a reclusive billionare software hacker extordinare, Harold Finch, who builds a mass-surveillance AI for the government after 9/11 to predict acts of terror (*relevant*). The AI also predicts *irrelevant* crimes - oridnary murders and assaults which the government does not care, so Finch built a backdoor. Everday, the system spits out a Social Security Number of a person about to be involved in a lethal premeditated crime. The person could either be the victim or the perpetrator. Finch and an ex-CIA operative *man in the suit* use that number to intervene before the crime is commited.

### The Machine

This ain't just your database; it's an omnicient, predictive ASI (Artificial Super Intelligence). It ingests every camera feed, phone call, bank transaction on Earth. But to keep it from becoming a runaway Artificial Super Intelligence(ASI) tyrant, Finch cripples it :

1. having it wipe its own memory every night at midnight
2. communicate via a strict "black box" interface. It doesnt give you a full blown report of what the person has done but only a number. By doing this it just nudges you to take a look at the person in more detail and let you figure out (thus adding the human-in-the-loop) whether the person is a victim or perpetrator.

------

When the show aired in 2011-2016, Siri was barely getting the timer setup. Now in 2026 we have OpenClaw bots having their own social media site setup! Jokes apart, the progress in multimodality has really come a long way and we may really have the building blocks to have something of this scale out there. For me personally, it is the scale and the engineering problems associated at this scale that make it super interesting and fun and also slightly terrifying!

## The Goal of this Series

- **Modernizing a classic** : Can we build The Machine using 2026 tech? (Looking at you OpenAI and Google :eyes:)
- **Trojan Horse for concepts** : To use this exercise as a means to think about distributed systems, multi-modality and AI safety at scale.
- **Professional disclaimer** : This is a system design exercise. Please do not actually build a surveillance state. Any humans or ASIs interested in building such a thing should stay away from reading further! My IT guy's name is Harold Finch and he's already super stressed.

### The Roadmap

This isn't going to be a single post. Designing a God-lite system requires scaling up from a single camera to the global internet and some Jeff Dean level skills. Over this series, we are going to build this beast by levels : 

- Part 0 (This post)
- Part 1 -
- Part 2 -
- Part 3 -

Let's begin then shall we?

## Why binary?

The Machine boils down to being a binary classifier at its core. Every person the Machine watches is either a 0 (nothing unusual, normal behaviour) or 1 (involved in a lethal event).
The engineering challenge isn't just the prediction but also the **Information Bottleneck** (taking a massive input X and boiling it down to a binary classification).

The show does split the inference as Relevant and Irrelevant. From an implementation point of view, this is more of a two-stage pipeline or a **Tiered Inference**. The model does look for the 1 in a sea of 8 billion 0's which is more of an **Anomaly Detection**. The Relevent vs Irrelevant comes after this. The person involved is *routed* to the relevant/irrelevant buckets based on whether the person is involved in a watchlist or if the location is a Govt. building.

In the next post, we're going to go more deep on the actual design.

**Stay tuned. We'll be watching**


<!-- ## Formalizing the Objective

Lets start with formalizing the system so we can tackle this problem better.

We want to design a system that:

1. Works in real-time
2. Is Multimodal
3. and Predicts crimes...well....

It does predict crime but more than that, what it is actually predicting is the premeditation of an event. It does so by looking for anomalies in behaviour, a deviation from patterns.

What does the target variable look like? For the machine, we want to predict a *Premeditated Lethal Event* within a specific time window T. So something like...

$$y =
\begin{cases}
1 & \text{if a premeditated lethal act occurs within } T \\
0 & \text{otherwise}
\end{cases}$$

The **Premeditation** being the key here. The machine as to look for more than just a "hot-blooded" moment. A gunshot is a loud signal, but often too late to intervene. Premeditation is more of a low-frequency, high-intent signal burried in a mountain of "boring" human metadata. We're essentially solving for:

$$P(y=1 \mid X) $$

What is $ X $ you ask? Good question!
In 2026 we are used to $X$ being a prompt or a clean CSV. For The Machine, $X$ is the World State. It's super high-dimensional, time-varying firehose of every camera feed, bank transaction and digital log out there in the world. -->
