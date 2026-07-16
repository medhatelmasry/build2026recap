# Coding with Microsoft Fondry Local

## What is Microsoft Foundry Local?

Foundry Local is a local AI solution that runs entirely on the user's device. It also provides an SDK (C#, JavaScript, Rust, and Python) that helps you build app that interact with Foundry Local.

## Installation

To install Foundry Local, follow these steps:

### Windows

```bash
winget install Microsoft.FoundryLocal
```

### macOS (only on silicon chips)

```bash
brew tap microsoft/foundrylocal
brew trust microsoft/foundrylocal
brew install foundrylocal
```

### CLI commands

Try the following Foundry Local CLI commands:

#### To detect the CLI version:

```bash
foundry --version
```

<details>
<summary>
Expected output:
</summary>
0.8.119
</details>

---

#### To view the list of CLI commands:

```bash
foundry --help
```

<details>
<summary>
Expected output:
</summary>
Description:<br />
  Foundry Local CLI: Run AI models on your device.
  
🚀 Getting started:
  
1. To view available models: foundry model list
2. To run a model: foundry model run <model>

EXAMPLES:<br />
   foundry model run phi-3-mini-4k

Usage:<br />
  foundry [command] [options]

Options:<br />
  -?, -h, --help  Show help and usage information<br />
  --version       Show version information<br />
  --license       Display foundry license information

Commands:<br />
  __model__    Discover, run and manage models<br />
  __cache__    Manage the local cache<br />
  __service__  Manage the local model inference service
</details>

___

#### To download a model into local cache:

```bash
foundry model download qwen2.5-0.5b
```

<details>
<summary>
Expected output:
</summary>
Downloading qwen2.5-0.5b-instruct-generic-gpu:4...

. . .  T R U N C A T E D . . .

[##################################  ]  94.85 % [Time remaining: about 1s]<br />  [##################################  ]  95.22 % [Time remaining: about 1s]<br />  [##################################  ]  95.59 % [Time remaining: about 1s]<br />[##################################  ]  95.96 % [Time remaining: about 1s]<br />[##################################  ]  96.33 % [Time remaining: about 1s]<br />[##################################  ]  96.69 % [Time remaining: about 1s]<br />[##################################  ]  97.06 % [Time remaining: about 1s]<br />[################################### ]  97.43 % [Time remaining: about 1s]<br />[################################### ]  97.79 % [Time remaining: about 1s]<br />[################################### ]  98.16 % [Time remaining: about 1s]<br />[################################### ]  98.53 % [Time remaining: about 1s]<br />[################################### ]  98.90 % [Time remaining: about 1s]<br />[################################### ]  99.27 % [Time remaining: about 1s]<br />[################################### ]  99.63 % [Time remaining: about 1s]<br />[####################################] 100.00 % [Time remaining: about 0s]<br />[####################################] 100.00 % [Time remaining: about 0s] 85.9 MB/s <br />
Tips:<br />
- To find model cache location use: foundry cache location<br />
- To find models already downloaded use: foundry cache ls
</details>

___
#### To list models in local cache:

```bash
foundry cache list
```

<details>
<summary>
Expected output:
</summary>
💾 qwen2.5-0.5b &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    qwen2.5-0.5b-instruct-generic-gpu:4
</details>

___
#### To remove a model from local cache:

```bash
foundry cache remove qwen2.5-0.5b
```

<details>
<summary>
Expected output:
</summary>
⚠️ This will delete model 'qwen2.5-0.5b (qwen2.5-0.5b-instruct-generic-gpu:4)' from cache.<br />
⚠️ Are you sure you want to delete this model from the local cache? (y/n)<br />
y<br />
Deleted model qwen2.5-0.5b-instruct-generic-gpu:4 from the cache.
</details>

___
#### To download an run a model:

```bash
foundry model run qwen2.5-0.5b
```

<details>
<summary>
Expected output:
</summary>
Downloading qwen2.5-0.5b-instruct-generic-gpu:4...<br />
[####################################] 100.00 % [Time remaining: about 0s]&nbsp;&nbsp;105.2 MB/s<br />
🕛 Loading model... <br />
🟢 Model qwen2.5-0.5b-instruct-generic-gpu:4 loaded successfully<br />
<br />
Interactive Chat. Enter /? or /help for help.<br />
Press Ctrl+C to cancel generation. Type /exit to leave the chat.<br />
<br />
Interactive mode, please enter your prompt<br />
> 
</details>

___
