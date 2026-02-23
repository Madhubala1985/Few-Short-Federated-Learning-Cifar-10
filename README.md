# Few-Shot Federated Learning: An Empirical Study under Extreme Data Scarcity

## Overview

This project presents a structured empirical analysis of Few-Shot Federated Learning (FSFL) using the CIFAR-10 dataset.

The study investigates what happens when two challenging constraints are combined:

- **Few-Shot Learning** — only a small number of labeled samples per class.
- **Federated Learning** — decentralized clients with non-IID data that cannot share raw samples.

Rather than proposing a new algorithm, this work focuses on understanding feasibility, limitations, and trade-offs when few-shot learning is applied in a federated environment.

---

## Project Structure

The experiments are organized into three stages:

### Stage 1 — Centralized Few-Shot Learning
- Prototype-based classification (metric learning approach)
- InceptionV3 backbone (ImageNet pretrained, frozen)
- Episodic evaluation
- 1-shot, 3-shot, and 5-shot settings

### Stage 2 — Standard Federated Learning
- 5 simulated non-IID clients
- 2 classes per client
- FedAvg aggregation
- Multi-round communication
- Client-wise accuracy tracking

### Stage 3 — Few-Shot Federated Learning
- 5-shot per class per client
- Prototype-based communication (no gradient sharing)
- Server-side prototype averaging
- Multi-round aggregation (10 rounds)
- Client-wise performance analysis
- Backbone comparison (InceptionV3 vs ResNet50)

---

## Key Results

| Setting | Accuracy |
|----------|----------|
| 5-shot Centralized Few-Shot | ~0.78 |
| Standard Federated Learning | ~0.96–0.97 |
| Few-Shot Federated Learning | ~0.18 |

### Observations

- Few-shot learning performs reasonably well in a centralized setting.
- Federated learning performs strongly when clients have sufficient local data.
- Combining both constraints results in significant performance degradation.
- Multi-round prototype aggregation does not substantially improve accuracy.
- Client-wise disparities persist under non-IID conditions.
- Backbone strength alone does not overcome representation bottlenecks.

---

## Experimental Insights

This study shows that:

- Prototype-based communication is highly communication-efficient.
- However, extreme data scarcity prevents meaningful knowledge accumulation.
- Frozen representations limit adaptation across heterogeneous clients.
- Repeated aggregation primarily recombines noisy few-shot statistics rather than improving class separation.

These findings highlight structural limitations in few-shot federated settings rather than implementation weaknesses.

---

## Repository Contents
