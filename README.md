# kmd-gpu-mining

**To mine Komodo with GPU, you will need 3 things:**

1. Komodod  
2. kmd-nomp   
3. zcash miner of your choice 

*Please note, komodod and kmd-nomp are required because there are currently no KMD mining pools.* 
*We will basically be setting up a local mining pool, as it is required for GPU mining support*

**A guide detailing installation of Komodod and KMD-nomp can be found here:**

https://github.com/xRobeSx/kmd-nomp

*Installation is for Ubuntu 14.04 +*

**Once Komodod and KMD-Nomp are running, you now have a stratum pool to point your GPU miners.**

Assuming that your GPU's are on the same computer as Komodod and KMD-Nomp, then you will need a Linux zcash miner.

Optiminer github is located here: https://github.com/Optiminer/OptiminerZcash



*Please note, if you install Komodod and KMD-Nomp on another computer/server, you can mine with GPU's on windows as well. 

*This will just requiring pointing your windows miners to 192.168.1.xxx:7777(komodod and KMD-Nomp) vs locally with (127.0.0.1:7777)*
