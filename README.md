# kmd-gpu-mining

To mine Komodo with GPU, you will need 3 things:

1. Komodod
2. kmd-nomp
3. miner of your choice 

Please note, steps 1 and 2 are required because there are currently no KMD pools. 


Step 1. Update

sudo apt-get update

sudo apt-get upgrade


Step 2. Install Dependencies for KMD

sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python zlib1g-dev wget bsdmainutils automake libboost-all-dev libssl-dev libprotobuf-dev protobuf-compiler libqt4-dev libqrencode-dev libdb++-dev ntp ntpdate


Step 3. Install Komodod

git clone https://github.com/jl777/komodo
cd komodo
./zcutil/fetch-params.sh
.zcutil/build.sh -j8   (replace 8 with number of CPU threads you want to use) (this will take some time.)


Step 4. Create and Modify komodo.conf

cd ..
mkdir .komodo
cd .komodo
nano komodo.conf

rpcuser=<yourRpcUserName>
rpcpassword=<yourRpcPassword>
rpcport=<YourRpcPort>
txindex=1
daemon=1
server=1
rpcallowip=127.0.0.1
addnode=5.9.102.210
addnode=78.47.196.146
addnode=178.63.69.164
addnode=88.198.65.74
addnode=5.9.122.241
addnode=144.76.94.38
blocknotify=node /home/<user>/z-nomp/scripts/cli.js blocknotify komodo %s

Ctrl+X, then Y to save. 


Step 5. Install kmd-nomp
cd ..
sudo apt-get install libsodium-dev npm redis-server
sudo npm install n -g
sudo n stable
git clone https://github.com/xrobesx/kmd-nomp
cd kmd-nomp
npm update
npm install

**if libsodium package not found (ubuntu 14.04)**
cd ..
git clone https://github.com/jedisct1/libsodium.git
cd libsodium
./configure
./autogen.sh
sudo make
sudo make install


Step 6. Restart Redis-server

cd ..
sudo service redis-server restart


Step 7. Edit blockTemplate.js to remove this.rpcData.founders (from zcash)

=>in file "z-nomp/node_modules/stratum-pool/lib/blockTemplate.js"
replace line 26 by
var blockReward = (this.rpcData.miner) * 100000000;

**if not done, it will generate error**


Step 8. KMD-NOMP Config Files

cd ..
cd kmd-nomp
cp config_example.json config.json
nano config.json

"website": {
        "enabled": true,
        "host": "127.0.0.1",
        "port": 8080,
        "stratumHost": "127.0.0.1",

Ctrl+X, then Y to save.






