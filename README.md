# Dockerised DirecT2V

This repository provides a Dockerised version of the [DirecT2V](https://github.com/cvlab-kaist/DirecT2V) project.

## Original Project

For the original codebase and further details, please visit the official repository:  
[DirecT2V by CVLAB-KAIST](https://github.com/cvlab-kaist/DirecT2V)

## Getting Started

### Prerequisites

- Docker installed on your machine.
- Access to a compatible GPU (NVIDIA recommended).

### Usage

To run the Dockerised version, use the following command:

```bash
./run.sh <gpu_id>
```

- Replace `<gpu_id>` with the ID of the GPU you want to use.  
  For example, use `0` for the default GPU.
- **Note:** Multi-GPU support is not configured in this implementation.

### Customizing Prompts

The file `data/test.json` contains a dictionary of prompts used by the model. Each key is a **high-level prompt** describing the overall animation, and the value is a **list of framewise prompts** detailing the transformation step by step.

Here is an example from `test.json`:

```json
{
    "A rocket launching into the sky.": [
        "A stationary rocket on a launch pad with smoke at the base.",
        "Smoke increases, and the rocket begins to shake slightly.",
        "Flames erupt from the base as the rocket starts to lift off.",
        "The rocket clears the launch pad, surrounded by smoke and flames.",
        "The rocket ascends steadily, leaving a trail of smoke behind.",
        "The rocket gains altitude, flames still visible at its base.",
        "The rocket climbs higher, with a clearer view of its exhaust trail.",
        "The rocket reaches the clouds, partially obscured by vapor.",
        "The rocket emerges above the clouds, surrounded by a clear blue sky."
    ]
}
```

### Adding Your Own Prompts

To customize the prompts:

1. Open the `data/test.json` file in a text editor.
2. Add a new **high-level prompt** (e.g., `"A caterpillar transforming into a butterfly."`).
3. Write a detailed list of **framewise prompts** for each step of the transformation.

For example:

```json
{
    "A caterpillar transforming into a butterfly.": [
        "A caterpillar crawling on a green leaf.",
        "The caterpillar begins to weave a cocoon around itself.",
        "The cocoon starts to take shape, enclosing the caterpillar.",
        "The cocoon hardens and becomes fully formed.",
        "Subtle movements are visible inside the cocoon.",
        "The cocoon begins to crack slightly at one end.",
        "The wings of a butterfly start to emerge from the cocoon.",
        "The butterfly slowly crawls out of the cocoon, wings still folded.",
        "The butterfly spreads its wings for the first time.",
        "The butterfly takes flight, leaving the empty cocoon behind."
    ]
}
```

Save the file and re-run the script. The output will reflect your customized prompts and their framewise progression.

### Model Configuration

The model settings have been optimized to follow the best practices outlined in the original project.