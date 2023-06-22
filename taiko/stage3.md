# Taiko T3
## On web

 1. [deposit TTKO](https://sepolia.etherscan.io/address/0x6375394335f34848b850114b66A49D6F47f2cdA8#writeProxyContract)
 2. Sign up to [alchemy](https://www.alchemy.com/) and create new app on sepolia 
 3. [Get sepolia ETH](https://sepoliafaucet.com/)
 4. Get VPS on:
 - [DigitalOcean](https://m.do.co/c/07d98f258feb) (200$ ref  trial credits)
 - [Hetzner](https://hetzner.cloud/?ref=4acuPUwi16aa) (€⁠20 ref  trial credits)
 - or your own choice

## On server


**update system**

    apt update && apt upgrade - y
**install docker**

    sudo -i
    cd $HOME
    
    apt update && apt install curl -y && apt purge docker docker-engine docker.io containerd docker-compose -y
    rm /usr/bin/docker-compose /usr/local/bin/docker-compose
    curl -fsSL https://get.docker.com -o get-docker.sh && sh get-docker.sh
    systemctl restart docker
    curl -SL https://github.com/docker/compose/releases/download/v2.5.0/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
    chmod +x /usr/local/bin/docker-compose
    ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
**check**

    docker -v

**install taiko node**
```
git clone https://github.com/taikoxyz/simple-taiko-node.git
cd simple-taiko-node
cp .env.sample .env
```
**setup .env**
```
nano .env
```
> DISABLE_P2P_SYNC=**true**
> 
> L1_ENDPOINT_HTTP=**https link from alchemy**
> 
> L1_ENDPOINT_WS=**wss link from alchemy**
> 
> ENABLE_PROVER=**true**
> 
> L1_PROVER_PRIVATE_KEY=**metamask private key**
> 
> ENABLE_PROPOSER=**true**
> 
> L1_PROPOSER_PRIVATE_KEY=**metamask private key**
> 
> L2_SUGGESTED_FEE_RECIPIENT=**metamask address**

**run the node**
```
docker compose up -d

```
**logs** 
```
docker compose logs -f

```
**current state**

http://[YOUR IP]:3000/d/L2ExecutionEngine/l2-execution-engine-overview?orgId=1&refresh=10s

**[official docs](https://taiko.xyz/docs/guides/)**
