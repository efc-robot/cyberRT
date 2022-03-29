> Migrate from Cyber [official repository](https://github.com/storypku/CyberRT)


<!-- # Introduction

Apollo Cyber RT is an open source, high performance runtime framework designed
specifically for autonomous driving (AD) scenarios. Based on a centralized
computing model, it is greatly optimized for high concurrency, low latency, and
high throughput in autonomous driving.

During the last few years of development of AD technologies, we have learned a
lot from our previous experience with Apollo. The industry is evolving and so is
Apollo. Going forward, Apollo has already moved from development to production.
With volume deployment in real world, we see demands for the highest level of
robustness and performance. That’s why we spent years building and perfecting
Apollo Cyber RT, which addresses those requirements of AD solutions.

Key benefits of using Apollo Cyber RT:

- Accelerate development
  - Well defined task interface with data fusion
  - Array of development tools
  - Large set of sensor drivers
- Simplify deployment
  - Efficient and adaptive message communication
  - Configurable user level scheduler with resource awareness
  - Portable with fewer dependencies
- Empower your own autonomous vehicles
  - The default open source runtime framework
  - Building blocks specifically designed for AD scenarios
  - Plug and play your own AD system -->

# Build/Installation

## Dependencies

You can run the following command to install CyberRT pre-requisites:

```bash
bash tools/install/install_prereqs.sh
```

`sudo` privilege is needed, and by default **Fast-DDS v1.5.0** is installed under
`/usr/local/fast-rtps/`.

## Install Bazel 
**bazel** is needed to build CyberRT. Refer to [Install bazel on Ubuntu](https://docs.bazel.build/versions/main/install-ubuntu.html)
 for more details.

Run the following:
```bash
sudo apt install apt-transport-https curl gnupg
curl -fsSL https://bazel.build/bazel-release.pub.gpg | gpg --dearmor > bazel.gpg
sudo mv bazel.gpg /etc/apt/trusted.gpg.d/
echo "deb [arch=amd64] https://storage.googleapis.com/bazel-apt stable jdk1.8" | sudo tee /etc/apt/sources.list.d/bazel.list
```
Then install bazel using apt.
```bash
sudo apt update && sudo apt install bazel

```
## Build
In the CyberRT root directory, run

```bash
source setup.bash
bazel build //...
bazel test //...
```

# Run examples
## Compile 
Compile examples use:
```bash
bazel build //examples/cyber/common_component_example/...
```
## Run

- Change `GLOG_alsologtostderr` from `0` to `1` in `cyber/setup.bash`
- Run `source cyber/setup.bash` in current console.

OR add environmental variable in the terminal
```
export GLOG_alsologtostderr=1
```

In terminal #1 run
```bash
cyber_launch start examples/cyber/common_component_example/common.launch
```
In terminal #2 run
```bash
bazel run  //examples/cyber/common_component_example:channel_test_writer
```
In terminal #3 run
```bash
bazel run //examples/cyber/common_component_example:channel_prediction_writer
```

# DDS in CyberRT
CyberRT中有两个模块与DDS有关。
- 节点的上下线和存活状态维护，相关代码位于./cyber/service_discovery/communication目录下。
- CyberRT支持三种通信方式，分别是Intra，Shm和rtps。其中Intra和Shm是CyberRT自行设计的，rtps即使用Fastrtps。相关代码位于./cyber/transport/rtps目录下。
# Documents

- [Apollo Cyber RT Quick Start](https://github.com/ApolloAuto/apollo/tree/master/docs/cyber/CyberRT_Quick_Start.md):
  Everything you need to know about how to start developing your first
  application module on top of Apollo Cyber RT.

- [Apollo Cyber RT Developer Tools](https://github.com/ApolloAuto/apollo/tree/master/docs/cyber/CyberRT_Developer_Tools.md):
  Detailed guidance on how to use the developer tools from Apollo Cyber RT.

- [Apollo Cyber RT API for Developers](https://github.com/ApolloAuto/apollo/tree/master/docs/cyber/CyberRT_API_for_Developers.md):
  A comprehensive guide to explore all the APIs of Apollo Cyber RT, with many
  concrete examples in source code.

- [Apollo Cyber RT FAQs](https://github.com/ApolloAuto/apollo/tree/master/docs/cyber/CyberRT_FAQs.md):
  Answers to the most frequently asked questions about Apollo Cyber RT.

- [Apollo Cyber RT Terms](https://github.com/ApolloAuto/apollo/tree/master/docs/cyber/CyberRT_Terms.md):
  Commonly used terminologies in Cyber RT documentation and code.

- [Apollo Cyber RT Python Wrapper](python/README.md): Develop projects in
  Python.

More documents to come soon!
