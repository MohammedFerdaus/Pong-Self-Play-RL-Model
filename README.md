# Pong Self-Play RL Model

This project implements a reinforcement learning (RL) agent capable of learning to play a fully custom-built Pong environment through self-play, without relying on any predefined strategies or external gameplay data.
Using Deep Q-Learning (DQN), the agent controls both sides of the Pong board during training, evaluates past versions of itself, and progressively improves its performance through experience.

What This Project Demonstrates
- How self-play can train agents in competitive two-player environments
- How neural networks approximate Q-values for real-time decision-making
- How replay buffers, target networks, and epsilon-greedy exploration stabilize DQN training
- How agents bootstrap skill by competing against older snapshots of themselve
- How custom game environments provide flexibility beyond fixed frameworks

Features
- Fully Custom Pong Engine: Built from scratch with Pygame
- Bot Opponents: Easy and hard difficulty bots for baseline evaluation
- Deep Q-Network: Convolutional neural network for Q-value estimation
- Self-Play Training: Agent trains by playing against checkpointed versions of itself
- Checkpoint Pool: Maintains top-performing models for curriculum learning
- Multiple Game Modes: AI vs AI, AI vs Bot, Human vs AI, Human vs Human
- Training Metrics: TensorBoard logging and model checkpointing for reproducible experiments
- Human Play Mode: Test your skills against the trained agent

File Descriptions
- agent.py - RL agent with training loop, epsilon-greedy exploration, and evaluation
- model.py - Deep Q-Network with convolutional layers for processing game frames
- buffer.py - Experience replay buffer with GPU/CPU memory optimization
- checkpoint.py - Checkpoint pool managing top-N models for self-play opponents
- game.py - Pong environment with Gymnasium interface and configurable players
- assets.py - Game objects (Paddle, Ball) with physics and collision detection
- train.py - Training script with hyperparameter configuration
- main.py - Inference script to watch trained models play

Game Controls (Human Mode)
- Player 1 (Right/Green): K (up), J (down)
- Player 2 (Left/Purple): E (up), F (down)

Architecture
Neural Network:
- Input: 3 stacked 84x84 grayscale frames
- 3 convolutional layers (32→64→64 filters)
- Fully connected layers (756 hidden units → 3 actions)

Training Algorithm:
- Double DQN with target network updates every 10,000 steps
- Experience replay with 200,000 transition buffer
- Epsilon-greedy exploration (1.0 → 0.15 with 0.995 decay)

Self-Play System:
- Agent alternates playing both sides each episode
- One player uses latest model, other uses random checkpoint
- Checkpoint pool maintains top 5 models ranked by performance

Training Tips
- Agent starts losing heavily (normal for first 50-100 episodes)
- By episode 100-200, should win against easy bots
- Competitive vs hard bots by episode 500-1000
- Training is CPU-intensive; ensure adequate cooling
- Model auto-saves every 20 episodes

Ideal For
- This repository is perfect for intermediate to advanced learners exploring reinforcement learning, developers interested in multi-agent systems, or anyone studying self-play architectures used in systems like AlphaGo and AlphaZero.

License: MIT License
