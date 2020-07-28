# Dubbo Demo

This directory contains basic usages of Dubbo to help Dubbo developers for debugging and smoke test purpose. If you are looking for Dubbo samples for study purpose, you should look into [here](https://github.com/apache/dubbo-samples) where you will find comprehensive usages for how to use Dubbo in different scenarios with the different features.

## How To Build

To build all demo applications from the source code, simply step into '*dubbo-demo*' directory and use maven to build:

```bash
mvn clean package
```

After build completes, a couple of fat jars are generated under '*target*' directory under each module directories, for example: '*dubbo-demo-api-provider-${project.version}.jar*' can be found under the directory '*dubbo-demo/dubbo-demo-api/dubbo-demo-api-provider/target*'.

## How To Run

Since the generated artifacts are fat jars backed by spring boot maven plugin, they can be executed directly with '*java -jar*', and since multicast is used for service registration, a necessary system property '**-Djava.net.preferIPv4Stack=true**' is required in order to registry and discover the demo service properly. 

Use '*dubbo-demo/dubbo-demo-api*' as an example, to start the provider '*dubbo-demo-api-provider*', execute the following command:

```bash
java -Djava.net.preferIPv4Stack=true -jar dubbo-demo-api-provider-${project.version}.jar
```

To run the consumer '*dubbo-demo-api-consumer*', execute the following command:

```bash
java -Djava.net.preferIPv4Stack=true -jar dubbo-demo-api-consumer-${project.version}.jar
```

# 几个需要弄明白的问题:
    
    - Dubbo 是如何与 ZooKeeper 等注册中心进行交互的？
    - Provider 与 Consumer 之间是如何交互的？
    - 为什么我们在编写业务代码的时候，感受不到任何网络交互？
    - Dubbo Provider 发布到注册中心的数据是什么？
    - Consumer 为何能正确识别？
    - 两者的统一契约是什么？
    - 这个契约是如何做到可扩展的？
    - 这个契约还会用在 Dubbo 的哪些地方？
    - 