# Autonomous Sparse Spiking Dynamics Enable Long-Term Complex Procedural Memory

This repository contains the official code implementation for the paper *Autonomous sparse spiking dynamics enable long-term complex procedural memory*.

## 📝 Project Overview

This project introduces **Spiking Autonomous Memory (SAM)**, a unified computational framework. SAM utilizes a "spiking temporal scaffold" grounded in discrete sparse spiking dynamics to effectively mitigate two core theoretical barriers faced by conventional continuous artificial neural networks (ANNs) in long-term complex procedural memory tasks.

This repository provides the complete code for testing and comparing 5 different network architectures across two distinct tasks (synthetic memory and real-world dance trajectory memory) under varying sequence lengths.

## 🗂️ Code Structure

The repository is organized based on the baseline models and task scenarios:

```text
├── rc/                         # Reservoir Computing (RC) baselines
│   ├── rc_bp_dance_exp.py      # RC model + BP + Dance trajectory task
│   ├── rc_bp_stimulation_exp.py# RC model + BP + Synthetic memory rask
│   ├── rc_bptt_dance_exp.py    # RC model + BPTT + Dance trajectory task
│   └── rc_bptt_stimulation_exp.py # RC model + BPTT + Synthetic 
├── rnn/                        # Continuous Recurrent Neural Network (RNN) 
│   ├── RNN_layers/             # Basic definitions for RNN layers
│   ├── rnn_bp_dance_exp.py     # RNN model + BP + Dance trajectory task
│   ├── rnn_bp_stimulation_exp.py # RNN model + BP + Synthetic memory rask
│   ├── rnn_bptt_dance_exp.py   # RNN model + BPTT + Dance trajectory task
│   └── rnn_bptt_stimulation_exp.py # RNN model + BPTT + Synthetic  memory rask
└── sam/                        # Spiking Autonomous Memory (SAM) core model
    ├── RNN_layers/             # Spiking neurons and multi-compartmental dendritic RNN definitions
    │   ├── rnn.py
    │   └── spike_neuron.py
    ├── chunk_rnn.py            chunking
    ├── config.py               # Hyperparameter configurations for models and experiments
    ├── main_chunk_rnn_dance_exp.py       # SAM model + Dance trajectory task
    └── main_chunk_rnn_stimulation_exp.py # SAM model + Synthetic  memory task
```
## 🚀 Included Models
Based on the code structure, this project supports the testing and comparison of the following 5 model configurations:

SAM (Spiking Autonomous Memory): The proposed spiking recurrent network framework based on multi-compartmental dendritic spiking neurons and a local predictive learning rule.

RC-BP: Continuous reservoir computing model, training only the output weights using standard Backpropagation (BP) with detached temporal feedback.

RC-BPTT: Continuous reservoir computing model trained using Backpropagation Through Time (BPTT).

RNN-BP: Continuous RNN, jointly optimizing recurrent and output weights using BP.

RNN-BPTT: Continuous RNN trained using global BPTT.

## 🎯 Evaluation Tasks
The repository evaluates models on two core tasks across varying sequence durations and pattern quantities:

Synthetic Memory Task (stimulation experiments): Requires models to autonomously generate high-dimensional, complex temporal patterns synthesized from superimposed sinusoidal waves with varying frequencies, phases, and amplitudes.

Real-World Memory Task (dance experiments): Uses human dance motion capture data from the FineDance dataset (132-dimensional continuous kinematic trajectories) to test the stable generation of complex, real-world procedural memory. 

Dataset Access: The data for this task is derived from the FineDance dataset. You can obtain the raw 3D full-body motion capture data from their official repository: [FineDance GitHub.](https://github.com/li-ronghui/FineDance)

## ⚙️ Quick Start
You can directly run the Python scripts in each subdirectory to start training and evaluating the corresponding models and tasks. For example:

Test the SAM model on the real-world dance task:

```Bash
cd sam
python main_chunk_rnn_dance_exp.py
```
Test the RC-BPTT baseline on the synthetic memory task:

```Bash
cd rc
python rc_bptt_stimulation_exp.py
```
(Tip: You can customize hyperparameters such as sequence duration, frequency, and the number of stored patterns directly within the experimental scripts, or change model configurations in sam/config.py.)



## 📖 Citation
If you use the dance experiments, please make sure to cite the FineDance dataset:
```代码段
@inproceedings{li2023finedance,
  title={FineDance: A Fine-grained Choreography Dataset for 3D Full Body Dance Generation},
  author={Li, Ronghui and Yang, Jianrong and Lin, Jiaming and others},
  booktitle={Proceedings of the IEEE/CVF International Conference on Computer Vision},
  pages={10234--10243},
  year={2023}
}
```
