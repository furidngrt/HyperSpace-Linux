# Hyperspace AIOS-CLI Tutorial

## Step 1: Install aios-cli
Run the installation command for Linux:

```bash
curl https://download.hyper.space/api/install | bash
```

```
source /root/.bashrc
```

This script will:
- Download the latest aios-cli binary.
- Install required GPU drivers if applicable.
- Place the binary in a directory in your system's PATH.

Verify the installation:

```bash
aios-cli version
```

This should output the installed version of aios-cli.

## Step 2: Start the aios-cli Daemon

Use `screen` to ensure the daemon runs 24/7, even if the session is closed. Start a new screen session:

```bash
screen -S aios-cli
```

Then, start the local daemon inside the screen session:

```bash
aios-cli start
```

To detach from the screen session and leave the daemon running, press `Ctrl+A` followed by `D`.

You can reattach to the screen session later using:

```bash
screen -r aios-cli
```

Check the daemon status:

```bash
aios-cli status
```

## Step 3: Download and Use Models

List available models:

```bash
aios-cli models available
```

Download a specific model (e.g., Mistral 7B):

```bash
aios-cli models add hf:TheBloke/Mistral-7B-Instruct-v0.1-GGUF:mistral-7b-instruct-v0.1.Q4_K_S.gguf
```

Run inference locally with the model:

```
screen -S infer
```

```bash
aios-cli infer --model hf:TheBloke/Mistral-7B-Instruct-v0.1-GGUF:mistral-7b-instruct-v0.1.Q4_K_S.gguf --prompt "Can you explain the concept of hyperspace and its applications in science fiction?"
```

CTRL+A+D

## Step 4: Connect to the Hive Network

Import your private key:

```
nano key.pem
```

```bash
aios-cli hive import-keys ./key.pem
```

Log in using your key:

```bash
aios-cli hive login
```

Connect to the network to start providing model inference:

```bash
aios-cli hive connect
```

If you encounter "Another instance is already running," ensure the daemon is running within the screen session started earlier.

## Step 5: Select a Tier and Start Earning Points

Choose a tier based on your system's resources:

```bash
aios-cli hive select-tier <tier_number>
```

Replace `<tier_number>` with the appropriate tier (1-5). For example, to select tier 5:

```bash
aios-cli hive select-tier 5
```

Download required models for the selected tier:

```bash
aios-cli models add hf:TheBloke/phi-2-GGUF:phi-2.Q4_K_M.gguf
```

Ensure you’re connected to the Hive network and earning points:

```bash
aios-cli hive points
```

Check private key & PubKey

```
aios-cli hive whoami
```


---

By following these steps and using `screen`, you ensure the aios-cli runs 24/7, even if you disconnect from the VPS. Reattach to the screen session as needed to monitor or manage the daemon.
