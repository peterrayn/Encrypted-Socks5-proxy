# Encrypted-Socks5-proxy

I try to encrypt the socks5 proxy by add some encryption algorithm in sake of enhance security and anonymity. Refer from shadowsocks structure but more easier and intelligible. It is the easy version of python. The code just for study purpose. 
<br>
<br>

# Introduction
<img src="img/constructure.jpg" alt="image" width="500">
There are two simple source file "local.py" and "server.py". <br>
The local.py should run on your PC to collect the network traffic with socks5 protocol.<br>
And the server.py should run on your remote server to catch the local request and relay it to target website.<br>
The encryption happened between the local to server,you can choose ChaCha20Poly1305,AESGCM or XOR. 
<br>
<br>
The configuration file parameter:

```
local_ip: "local.py" listen address,should be "127.0.0.1"
local_port: "local.py" listen port,"0-65535"
server_ip: "server.py" listen address,you should fill the public IPV4
server_port: "server.py" listen port,"0-65535"
password: use to encrypt the network data and authorizaion.
buffer: the maximum bytes of one analysis
encrypt_num: 0 -no encryption, 1 -Ploy1305, 2 -AESGCM, 3 -XOR  (0 and 3 not safe)
monitor_flow: true -monitor the data content, false -just show the length of it
```
# Usage

<br>

### -->Window(PowerShell) 


clone the project and enter the directory:
```bash
git clone https://github.com/peterrayn/Encrypted-Socks5-proxy.git
cd Encrypted-Socks5-proxy
```
<br>

```bash
change the configuration file (src\configuration.json)
refer above content "The configuration file parameter"
```
<br>

run in a new environment(optional):
 ```bash
python -m venv env
./env/Scripts/Activate.ps1
```
<br>

install the dependance:
```bash
pip install cryptography
```
<br>

run local file:
 ```bash
python src/local.py
```
<br>

OR run server file:
 ```bash
python src/server.py
```

<br>

### -->MAC or Linux

```bash
git clone https://github.com/peterrayn/Encrypted-Socks5-proxy.git
cd Encrypted-Socks5-proxy
```
<br>

configure it
```bash
vim src/configuration.json
```
<br>

```
python3 -m venv env
source env/bin/activate
pip install cryptography
```
<br>

run local file:
 ```bash
python3 src/local.py
```
OR run server file:
 ```bash
python3 src/server.py
```

After successfully run two python file, you can use browser extensions or v2rayN to send the network data.


