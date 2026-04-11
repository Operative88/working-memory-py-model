# Working Memory Model

A biologically-inspired neural network model that demonstrates how information can be stored and maintained through recurrent synaptic connections, inspired by research on cortical working memory mechanisms.

## Overview

This project implements a computational model of working memory based on the influential work of Compte et al. (2000). The model shows how a spiking neural network can maintain information about external stimuli in its neural activity patterns, even after the stimulus has been removed. This maintenance occurs through recurrent connections within and between populations of excitatory and inhibitory neurons.

## Key Features

- **Spiking Neural Network Simulation**: Implements realistic neuron models with spike generation and temporal dynamics
- **Recurrent Architecture**: Excitatory and inhibitory populations with recurrent and cross-inhibitory connections
- **Stimulus and Distractor Support**: Ability to present stimuli and distractors at different times and intensities
- **Monitoring and Analysis**: Comprehensive spike monitoring and neural activity tracking for analysis
- **Configurable Parameters**: Highly parameterized to explore different network configurations

## How It Works

The model consists of:
- An excitatory population of pyramidal neurons arranged with a preferred direction dimension
- An inhibitory population of interneurons
- External Poisson input representing background neural activity
- Recurrent connections with Gaussian weight profiles to implement selective persistent activity

When a stimulus is presented, the network develops a hill of activity centered around the stimulus location. Through recurrent connections, this activity pattern is maintained even after stimulus removal, implementing a neural mechanism for working memory.

## Installation

1. Clone this repository:
   ```bash
   git clone <repository-url>
   cd Model-pamieci-roboczej
   ```

2. Create a virtual environment (recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Dependencies

- **brian2**: Spiking neural network simulator
- **numpy**: Numerical computing
- **scipy**: Scientific computing utilities
- **matplotlib**: Visualization and plotting
- **neurodynex3**: Neuroscience simulation tools

## Usage

```python
from wm_model import simulate_wm

# Run simulation with default parameters
results = simulate_wm()

# Access simulation results
rate_monitor_excit, spike_monitor_excit, voltage_monitor_excit, idx_monitored, \
rate_monitor_inhib, spike_monitor_inhib, voltage_monitor_inhib, idx_monitored_inhib, \
weight_profile = results
```

### Customizing Simulations

The `simulate_wm()` function accepts numerous parameters to customize the simulation:

- **Population sizes**: `N_excitatory`, `N_inhibitory`
- **External input**: `N_extern_poisson`, `poisson_firing_rate`
- **Stimulus parameters**: `stimulus_center_deg`, `stimulus_width_deg`, `stimulus_strength`, `t_stimulus_start`, `t_stimulus_duration`
- **Distractor parameters**: Similar to stimulus parameters for adding distractors
- **Synaptic weights**: `G_inhib2inhib`, `G_inhib2excit`, `G_excit2excit`, `G_excit2inhib`
- **Simulation duration**: `sim_time`

## Scientific Background

This implementation is based on:

Compte, A., Brunel, N., Goldman-Rakic, P. S., & Wang, X. J. (2000). "Synaptic mechanisms and network dynamics underlying spatial working memory in a cortical network model." *Cerebral Cortex*, 10(9), 910-923.

This foundational paper demonstrated how recurrent synaptic connections can implement working memory through persistent neural activity - a mechanism widely observed in prefrontal cortex during working memory tasks.

## Project Structure

```
Model-pamieci-roboczej/
├── README.md              # This file
├── requirements.txt       # Python dependencies
├── wm_model.py           # Main simulation code
└── .git/                 # Version control
```

## References

- Compte et al., 2000 - Foundational work on working memory networks
- Brian2 Documentation: https://brian2.readthedocs.io/
- Neuroscience simulation tools: https://neuronunit.scidash.org/