# Hyperliquid
To set up a Hyperliquid validator node, you will need a machine with the following system requirements:

- **Operating System**: Ubuntu 24.04
- **CPU**: 4 cores
- **RAM**: 16 GB
- **Storage**: 50 GB SSD

### Step-by-Step Setup:

1. **Create a non-root user**:
    ```bash
    sudo adduser hlnode
    sudo usermod -aG sudo hlnode
    su - hlnode
    ```

2. **Download configuration files**:
    ```bash
    curl https://binaries.hyperliquid.xyz/Testnet/initial_peers.json > ~/initial_peers.json
    echo '{"chain": "Testnet"}' > ~/visor.json
    curl https://binaries.hyperliquid.xyz/Testnet/non_validator_config.json > ~/non_validator_config.json
    curl https://binaries.hyperliquid.xyz/Testnet/hl-visor > ~/hl-visor
    chmod a+x ~/hl-visor
    ```

3. **Install dependencies**:
    ```bash
    sudo apt update
    sudo apt install screen
    ```

4. **Run the node**:
    Use a screen session to run the node in the background:
    ```bash
    screen -S hlnode
    ~/hl-visor
    ```
    To detach from the screen session, press `Ctrl + A + D`.

5. **Monitor the node**:
    - To check the storage used by the node:
      ```bash
      du -hs hl
      ```
    - You can also inspect the data folder:
      ```bash
      cd ~/hl/data && ls
      ```

6. **Reattach to the session**:
    If you need to return to the session, use:
    ```bash
    screen -r hlnode
    ```

By following these steps, your node should be up and running, and you can monitor its performance through various commands.
