# Pong-Self-Play-RL-Model

This project implements a reinforcement learning (RL) agent capable of learning to play a fully custom-built Pong environment through self-play, without relying on any predefined strategies or external gameplay data.
Using Deep Q-Learning (DQN), the agent controls both sides of the Pong board during training, evaluates past versions of itself, and progressively improves its performance through experience.

The goal of the project is to demonstrate:
- How self-play can be used to train agents in competitive two-player environments
- How neural networks can approximate Q-values for continuous, real-time decision-making
- How techniques such as replay buffers, target networks, and epsilon-greedy exploration stabilize DQN training
- How an agent can bootstrap its skill level by competeing against older snapshots of itself
- How custom environments provide flexibility beyond fixed frameworks like OpenAI Gym

The project includes:
- A fully custom Pong game engine built from scratch
- Easy and hard bot opponents for baseline training
- A deep neural network model for Q-value estimation
- A single-sided and full self-play training pipeline
- A snapshot-based opponent pool for progressive skill improvement
- A human-play mode allowing you to compete against the trained agent
- Logging, metrics, and model checkpointing for reproducible experiments

This repository is ideal for intermediate to advanced learners exploring reinforcement learning, developers interested in multi-agent systems, or anyone studying self-play architectures used in systems like AlphaGo and AlphaZero.
