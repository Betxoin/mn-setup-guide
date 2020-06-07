![Example-Logo](https://i.imgur.com/78X4xET.png)
# Betxoin Masternode Setup Guide (Ubuntu 16.04)
This guide will assist you in setting up a Betxoin Masternode on a Linux Server running Ubuntu 16.04.

If you require further assistance contact the support team [Discord](https://discord.gg/wqkrZsV)
***
## Requirements
1) **1000 Betxoin coins (buy on [Crex24](https://crex24.com/?refid=5q0v5tcmmzqq9q1wvy3h))**
2) **VPS (Vultr) running Linux Ubuntu 16.04**
3) **Windows or MAC OS X local wallet**
4) **SSH client such as [Bitvise](https://dl.bitvise.com/BvSshClient-Inst.exe)**
***
## Contents
* [Section A](#Section-A) - Creating the VPS within [Vultr](https://www.vultr.com/?ref=7485061)
* [Section B](#Section-B) - Downloading and installing Bitvise
* [Section C](#Section-C) - Connecting to the VPS and Getting the Ubuntu Server ready via Bitvise
* [Section D](#Section-D) - Preparing the local wallet
* [Section E](#Section-E) - Editing the configs
* [Section F](#Section-F) - Starting the masternode
***

## <a name = "Section-A"></a> Section A - Creating the VPS within [Vultr](https://www.vultr.com/?ref=7485061) 
***Step 1***
* Register at [Vultr](https://www.vultr.com/?ref=7485061)
***

***Step 2***
* After you have added funds to your account go [here](https://my.vultr.com/deploy/) to create your Server
***

***Step 3*** 
* Choose a server location (preferably somewhere close to you)

![Example-Location](https://i.imgur.com/tMZzsSi.png)
***

***Step 4***
* Choose a server type: 64 bit OS -> Ubuntu 16.04

![Example-OS](https://i.imgur.com/Nk4NwON.png)
***

***Step 5***
* Choose a server size: $5/mo will be fine 

![Example-OS](https://i.imgur.com/iptKUoa.png)
***

***Step 6*** 
* Set a Server Hostname & Label (name it whatever you want)

![Example-hostname](https://i.imgur.com/jLGo9aq.png)
***

***Step 7***
* Click "Deploy now"

![Example-Deploy](https://i.imgur.com/5OZTu69.png)
***


[:arrow_up: Contents :arrow_up:](#Contents)


## <a name = "Section-B"></a> Section B - Downloading and installing BitVise

***Step 1***
* Download Bitvise [here](https://dl.bitvise.com/BvSshClient-Inst.exe)
***

***Step 2***
* Select the correct installer depending upon your operating system. Then follow the install instructions

![Example-BitviseInstaller](https://i.imgur.com/t3Liiza.png)
***


[:arrow_up: Contents :arrow_up:](#Contents)


## <a name = "Section-C"></a> Section C - Connecting to the VPS and Getting the Ubuntu Server ready via Bitvise

***Step 1***
* Click on your server
![Example-Vultr](https://i.imgur.com/ndIUukY.png)
***

***Step 2***
* Copy your VPS IP
![Example-Vultr](https://i.imgur.com/yS3flWi.png)
***

***Step 3***
* Open the bitvise application and fill in the "Host" box with the IP

![Example-BitviseInstaller](https://i.imgur.com/3lYJcTg.png)
***

***Step 4***
* Copy the root password from the VULTR server page
![Example-RootPass](https://i.imgur.com/V7o6Qr8.png)
***

***Step 5***
* type "root" as the username
* type "password" as the Initial method
* type password
* then press "Login"

![Example-RootPass](https://i.imgur.com/1a4v0z5.png)

* then press "Accept and Save"

![Example-RootPass](https://i.imgur.com/YUDVBxR.png)
***

***Step 6 (Updating)***
* Paste the code below into the Bitvise terminal then press enter

```
sudo apt-get update
```

![Example-RootPassEnter](https://i.imgur.com/oT7yGpI.png)
***

***Step 7 (Install all required libraries)***

***Step 7.1*** Paste the code below into the Bitvise terminal then press enter:

```
sudo apt-get install git automake build-essential libtool autotools-dev autoconf pkg-config libssl-dev libboost-all-dev software-properties-common
```

![Example-RootPassEnter](https://i.imgur.com/qQbf6Cm.png)

When prompted do you want to continue? [Y/n]

Enter `Y` and press enter

![Example-RootPassEnter](https://i.imgur.com/72WE2NN.png)


***Step 7.2*** Paste the code below into the Bitvise terminal then press enter:

```
sudo add-apt-repository ppa:bitcoin/bitcoin
```

![Example-RootPassEnter](https://i.imgur.com/9iXZ1HI.png)

Press enter to continue

![Example-RootPassEnter](https://i.imgur.com/31chgOz.png)


***Step 7.3*** Paste the code below into the Bitvise terminal then press enter:

```
sudo apt-get update
```

![Example-RootPassEnter](https://i.imgur.com/3foqMbp.png)

***Step 7.4*** Paste the code below into the Bitvise terminal then press enter:

```
sudo apt-get install libdb4.8-dev libdb4.8++-dev libminiupnpc-dev
```

![Example-RootPassEnter](https://i.imgur.com/ID3NQdv.png)

When prompted do you want to continue? [Y/n]

Enter `Y` and press enter

![Example-RootPassEnter](https://i.imgur.com/srHJwVt.png)
***

***Step 8 (download daemon on VPS)***

***Step 8.1*** Paste the code below into the Bitvise terminal then press enter:

```
wget https://github.com/Betxoin/Betxoin/releases/download/v2.0/betxoin-daemon-linux64.tar
```

![Example-RootPassEnter](https://i.imgur.com/zQ99t3g.png)

***Step 8.2*** Paste the code below into the Bitvise terminal then press enter:

```
tar -xvf betxoin-daemon-linux64.tar
cd betxoin
chmod -f 777 betxoind 
chmod -f 777 betxoin-cli 
chmod -f 777 betxoin-tx 
./betxoind 
```

![Example-RootPassEnter](https://i.imgur.com/QlKP43z.png)

Once you’ve run the Daemon for the first time - it will show you to setup a rpcuser and rpcpassword and close right after it - it has also created the folder structure where the blockchain and all config files are going to be. 
***


[:arrow_up: Contents :arrow_up:](#Contents)


## <a name = "Section-D"></a> Section D - Preparing the local wallet

In your Wallet-App go to: Tools -> Debug console.  

![Example-Debugconsole](https://i.imgur.com/s15ZcsI.png)

follow these steps:


***Step 1*** Paste the code below into the Debug console then press enter:

```
getnewaddress MN1
```

answer: BJTCmtBa5931vcsU9a1zF3PUaqyxeZwzLi

![Example-getnewaddress](https://i.imgur.com/g2sqqX3.png)


***Step 2*** Paste the code below into the Debug console then press enter:

```
sendtoaddress BJTCmtBa5931vcsU9a1zF3PUaqyxeZwzLi 1000
```

answer: fa003f2643f1ef7cc14b16f5908eb0ef7dd38dd05ec3495d7bf5546a07db8460

![Example-sendtoaddress](https://i.imgur.com/34NIBZA.png)

Wait for the transaction to have at least 15 confirmations before continuing.

![Example-confirmations](https://i.imgur.com/lE5MXRP.png)


***Step 3*** Paste the code below into the Debug console then press enter:

```
masternode genkey
```

answer: 877YKiii5TXMjYNvCyUdXYnuKysUn5VP47bkwqWRPcQ6idwtJBf

![Example-genkey](https://i.imgur.com/7euxFc2.png)


***Step 4*** Paste the code below into the Debug console then press enter:

```
masternode outputs
```

answer: 
  "txhash" : "fa003f2643f1ef7cc14b16f5908eb0ef7dd38dd05ec3495d7bf5546a07db8460",
  "outputidx" : 1

![Example-outputs](https://i.imgur.com/N5wBLxY.png)


[:arrow_up: Contents :arrow_up:](#Contents)


## <a name = "Section-E"></a> Section E - Editing the configs


***Step 1*** Editing the configs via Bitvise terminal

Paste the code below into the Bitvise terminal then press enter:

```
apt-get install nano
```

![Example-nano](https://i.imgur.com/6UEng5S.png)

Nano is a great console-based text-editor 

Let’s open the betxoin.conf located in the .BETXOIN folder 

This folder was created by the daemon on the first run! 

Paste the code below into the Bitvise terminal then press enter:

```
nano /root/.BETXOIN/betxoin.conf
```

![Example-conf](https://i.imgur.com/WQv1vc1.png)

This is configuration for masternode setup:

```
rpcuser={CHOOSE A RANDOM USER}
rpcpassword={CHOOSE A RANDOM PASSWORD}
rpcallowip=127.0.0.1
port=30300
rpcport=30400
listen=1
server=1
daemon=1
maxconnections=256
masternode=1
externalip={YOUR SERVER IP}
masternodeprivkey={YOURPRIVKEY - WE WILL GET THAT LATER}
logtimestamps=1
masternodeaddr={YOUR SERVER IP}
```

which should result in something like that:

![Example-conf](https://i.imgur.com/drixtzF.png)

Save the config (Ctrl+X --> Y --> Enter)

`Ctrl+x`

![Example-conf](https://i.imgur.com/YS2dlce.png)

`Y`

![Example-conf](https://i.imgur.com/aYM5XzN.png)

`Enter`

![Example-conf](https://i.imgur.com/8qEAIju.png)


***Step 2*** Editing the configs in your Wallet-App

Go to the tools tab within the wallet and click open "masternode configuration file"

![Example-configuration](https://i.imgur.com/gKZQLa2.png)

* Fill in the form  
* For `Alias` type something like "MN1" don't use spaces  
* The `Address` is the IP and port of your server (this will be in the putty terminal that you still have open)  
* The `PrivKey` is your masternode private key (This is also in the putty terminal that you have open)  
* The `TxHash` is the transaction ID/long key that you copied to the text file  
* The `Output Index` is the 0 or 1 that you copied to your text file  

![Example-configuration](https://i.imgur.com/92WYWtx.png)

Click "File Save"


[:arrow_up: Contents :arrow_up:](#Contents)


## <a name = "Section-F"></a> Section F - Starting the masternode


***Step 1*** Starting the daemon on the Ubuntu server:

```
cd betxoin
./betxoind
```

The daemon should start minimized.   
You’ll only see a message like this:   

```
BETXOIN server starting
```

![Example-starting](https://i.imgur.com/jMwLGQ6.png)

wait for the full sync before continuing:

```
./betxoin-cli mnsync status
```

You should see: "RequestedMasternodeAssets" : 999, (this means full sync)

![Example-mnsync](https://i.imgur.com/X4xoXJU.png)

***Step 2*** Move on your Wallet-App

* Close out of the wallet and reopen Wallet  
* Wait for the full sync 
* Go to the Debug console  
* Type the command below and press enter  

```
startmasternode alias 0 MN1
```

![Example-startmasternode](https://i.imgur.com/V9tuETQ.png)


***Step 3*** Check the status of your masternode within the VPS by using the command below:

```
./betxoin-cli masternode status
```

You should see

![Example-status](https://i.imgur.com/bARphJN.png)

If you do, congratulations! You have now setup a masternode.  
If you do not, please contact me or any other support

[:arrow_up: Contents :arrow_up:](#Contents)
