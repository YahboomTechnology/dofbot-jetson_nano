## Porting and Compiling the Advanced Vision Package

Note: Since the content of this chapter is part of the theoretical curriculum, the corresponding package has not been pre-installed within the system image. You must port the package into the image and compile it before you can run it. Please refer to the steps below to port and compile the package.

### 1. Step 1: Copy the Package to the Mainboard

Use the WinSCP tool or the `scp` command to copy the `dofbot_pro_vision` source package—located within the program source code directory—to the `home` directory on your mainboard. Typically, the paths are:

Raspberry Pi 5 Mainboard: `/home/pi`

Jetson Nano Mainboard: `/home/jetson`

### 2. Step 2: Copy the Package into the Docker Container

Next, open a terminal on the mainboard and enter the following command to copy the package from the mainboard into the `src` directory of the Docker container's workspace:

```shell
cd
docker cp ~/dofbot_pro_vision <Container Name or ID>:/root/dofbot_ws/src
```

### 3. Step 3: Compile the Package

Finally, enter the following command in the mainboard terminal to access the terminal inside the Docker container:

```shell
docker exec -it <Container Name or ID> /bin/bash
```

Once inside the container, enter the following commands to compile the package:

```shell
cd ~/dofbot_ws
colcon build --packages-select dofbot_pro_vision
```