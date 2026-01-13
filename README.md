# Master_Thesis
Conflict Resolution in Train Timetabling Using Alternative Graphs and Deep Q-Networks


This repository contains all code, data, and scripts used in my Master's thesis on applying reinforcement learning (RL) to microscopic train timetable conflict resolution. The goal is to construct an Alternative Graph (AG) representation from real railway data and train an RL agent that quickly generates feasible conflict-resolution decisions, and to compare its performance with baseline methods.

---

## 📁 Repository Structure
├── Data_from_LUKS/
├── Delay_Cap_120_Scripts/
├── Hyperparameter_tuning_Script/
├── Input_File_Generation/
├── Input_data/
├── ModelA_Scripts/
├── ModelB_Scripts/
├── ModelC_Scripts/
├── Neural_Network_Scripts/
├── plot_generation.py
└── README.md



---

## 🔍 What Each Folder Contains

### 📌 `Data_from_LUKS/`

Contains raw infrastructure and timetable data exported from the LUKS system.  
These are used as the **original input** for preprocessing and graph construction.

Files here include:
- infrastructure element lists
- timetable exports
- block sequences

---

### 🛠 `Input_File_Generation/`

Scripts to process the raw LUKS data and generate the **input files** needed by the models.

Typical steps:
1. Normalize raw data
2. Build track segment mappings
3. Export processed CSV/JSON formats for later stages

Run these scripts **before training or evaluation**.

---

### 📂 `Input_data/`

Store **intermediate and train/test dataset files** after preprocessing.  
These are the files used by AG construction and RL training.

This folder is read by multiple scripts in other folders.

---

### 🤖 Model Script Folders

These folders contain scripts for specific model configurations:

#### 📦 `ModelA_Scripts/`
Training and evaluation routine for **Model A** (baseline reward design).

#### 📦 `ModelB_Scripts/`
Scripts implementing **Model B** with adjusted reward shaping and improvements.

#### 📦 `ModelC_Scripts/`
Contains code for **Model C**, which includes curriculum learning and advanced shaping.

Each folder typically contains:
- training loop scripts  
- evaluation and metric computation  
- model checkpoint saving

---

### 🧠 `Neural_Network_Scripts/`

Core neural network definitions and utilities shared across all models.

These include:
- network architecture (layers, activations)
- replay buffer
- optimizer setup
- model loading/saving functions

---

### ⚙️ `Delay_Cap_120_Scripts/`

Experiments and evaluation **with a 120s delay cap** applied.

Use these scripts to:
- test robustness against delay thresholds
- generate performance curves
- compare delay-capped vs uncapped results

---

### 📊 `Hyperparameter_tuning_Script/`

Contains scripts for **systematic hyperparameter tuning** such as:
- learning rate sweeps
- reward weight adjustments
- exploration schedule tuning

Use this folder to find the best configuration before training main models.

---

### 📈 `plot_generation.py`

Standalone script to create all evaluation plots used in the thesis.  
It reads evaluation results and generates:
- learning curves
- delay histograms
- comparisons between models
- OptDis benchmarking plots

Run it after training and evaluation, e.g.:

```bash
python plot_generation.py --input_dir results/ --output_dir figures/


