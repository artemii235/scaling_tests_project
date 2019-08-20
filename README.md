To build test blockchain docker image (--no-cache flag is optional when you making some changes in deps mostly):

docker build -f Dockerfile.blockchain --no-cache -t testblockchain .

Run as (exposes single node on port 7000 to connect to):

docker run -p 127.0.0.1:7000:7000 -d --mount src=/home/tony/.zcash-params,target=/root/.zcash-params,type=bind testblockchain

Note that you should mount zcash-params from somewhere! As an alternative you might add fetch-params.sh to your zip with daemon and execute it before start_blockchain.py script start. But note that it'll consume A LOT of network traffic.

If you want to use some custom daemon and start_blockchain.py - change it in Dockerfile.blockchain (wget http://159.69.45.70/FSM_latest.zip && unzip FSM_latest.zip && wget http://159.69.45.70/start_blockchain.py)