
### dappnode ==> Packages ==> Sepolia Geth ==> Config, Save the `ENV VALUE` of `EXTRA_OPTIONS`

![image](https://github.com/ruesandora/PowerPool/assets/101149671/139f54ad-c22c-4b50-bc12-8ee2a5de648b)

### dappnode ==> Packages ==> Sepolia Geth ==> We write `--snapshot=false` in the EXTRA_OPTIONS section in Config and click update. After 288 blocks have passed.
### Now what we're going to do is wait for 288 blocks to pass like this... 

![image](https://github.com/ruesandora/PowerPool/assets/101149671/25cc8232-27a5-496a-bba8-28fe68acea9f)


### dappnode ==> Packages ==> Sepolia Geth ==> We note the block height in Logs. 

![image](https://github.com/ruesandora/PowerPool/assets/101149671/f4605b28-0efd-471a-ac79-57e29b963296)




### dappnode ==> Packages ==> Sepolia Geth ==> We write `snapshot prune-state` in the EXTRA_OPTIONS section in Config and click update. We are waiting for the pruning process to be done

![image](https://github.com/ruesandora/PowerPool/assets/101149671/ca5b2ec7-7347-4bc2-b681-34b0369aa132)


### Writing state bloom to disk name=/sepolia/geth/statebloom.0x409490d515d3f315bea34e05f1e0fe522c56ea44a849fffff38b1cf9d27c2e9f.bf.gz. 
### It already says how many minutes are left on the far right where it says `eta`, wait for this process to complete.

### dappnode ==> Packages ==> Sepolia Geth ==> Remove in Info and delete the whole file.

![image](https://github.com/ruesandora/PowerPool/assets/101149671/b2b54733-5fc4-40d0-832c-2046b991202e)

### dappnode ==> Packages ==> Sepolia Geth ==> In the EXTRA_OPTIONS section in Config we write `--syncmode=snap --datadir=statebloom.0x409490d515d3f315bea34e05f1e0fe522c56ea44a849fffff38b1cf9d27c2e9f.bf.gz.` and click update. 

### dappnode ==> Expect Sepolia Geth sync on Dashboard 
![image](https://github.com/ruesandora/PowerPool/assets/101149671/e0fca72a-6d7f-488f-8d14-4e10008d42d9)


![image](https://github.com/ruesandora/PowerPool/assets/101149671/9f4736e6-a908-4c00-8102-521b4b0c2ed9)

### We are waiting for it to sync. This is the pruning process.

> Now restart PowerArgent and everything should be back to normal




