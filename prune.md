
### dappnode ==> Packages ==> Sepolia Geth ==> Config, Save the `ENV VALUE` of `EXTRA_OPTIONS`

![image](https://github.com/ahmkah/PowerPool_Pruning/assets/99053148/d5f89e82-e670-4f18-bb09-b3ea1b2d0039)

### dappnode ==> Packages ==> Sepolia Geth ==> Remove in Info and delete the whole file.

![image](https://github.com/ahmkah/PowerPool_Pruning/assets/99053148/614d9ec5-3b58-4544-b4a3-eb141be8c86e)

### dappnode ==> Packages ==> Sepolia Geth ==> We write `--snapshot=false` in the EXTRA_OPTIONS section in Config and click update. We are waiting for sync.

![image](https://github.com/ahmkah/PowerPool_Pruning/assets/99053148/07ebdbda-02ae-4299-9591-7febda52296a)

### dappnode ==> Expect Sepolia Geth sync on Dashboard 
![image](https://github.com/ahmkah/PowerPool_Pruning/assets/99053148/b8cec9d1-bbaf-4667-96f5-960cd75c8d83)

![image](https://github.com/ahmkah/PowerPool_Pruning/assets/99053148/4a55f196-b596-4357-8e13-63a11071e9ed)

### dappnode ==> Packages ==> Sepolia Geth ==> We note the block height in Logs. 

![image](https://github.com/ahmkah/PowerPool_Pruning/assets/99053148/4b9df6ed-50e2-4a0f-88dc-de0854238b28)

### Now what we're going to do is wait for 288 blocks to pass like this... After 288 blocks have passed 

### dappnode ==> Packages ==> Sepolia Geth ==> We write `snapshot prune-state` in the EXTRA_OPTIONS section in Config and click update. We are waiting for the pruning process to be done

![image](https://github.com/ahmkah/PowerPool_Pruning/assets/99053148/310c1be2-cfee-4b4e-baa5-b2a1f377aca1)

### Writing state bloom to disk name=/sepolia/geth/statebloom.0x409490d515d3f315bea34e05f1e0fe522c56ea44a849fffff38b1cf9d27c2e9f.bf.gz. 
### It already says how many minutes are left on the far right where it says `eta`, wait for this process to complete.

### dappnode ==> Packages ==> Sepolia Geth ==> In the EXTRA_OPTIONS section in Config we write `--http.api eth,engine,net,web3,txpool, --ws.api eth,engine,net,web3,txpool` and click update. 
### We are waiting for it to sync. This is the pruning process.

> Now restart PowerArgent and everything should be back to normal




