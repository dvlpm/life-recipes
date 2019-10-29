Fix slow docker on macOS
========================
With this step-by-step instruction you can enjoy high speed docker on macOS
-----------------------

1. Run recovery mode (Restart then cmd+R)
2. Open Utils->terminal
3. Run command
    ```bash
    spctl kext-consent add VB5E2TV963
    ```
4. Restart mac
5. Download and install [virtualbox](https://download.virtualbox.org/virtualbox/6.0.10/VirtualBox-6.0.10-132072-OSX.dmg)
6. Open terminal and run
    ```bash
    brew install docker docker-machine docker-machine-nfs
    ```
7. Run
    ```bash
    docker-machine create --driver virtualbox default
    ```
8. If docker machine already created then run
    ```bash
    docker-machine rm default
    docker-machine create --driver virtualbox default
    ```
9. Run
    ```bash
    docker-machine-nfs default
    ```

If you see this warning
```bash
exports:3: exported dir/fs mismatch: /Users /System/Volumes/Data
```
Then you should run docker-machine like this
```bash
docker-machine-nfs default --shared-folder=/System/Volumes/Data/Users --force
```

As result you should see this

```bash

 The docker-machine 'default'
 is now mounted with NFS!

 ENJOY high speed mounts :D

```
