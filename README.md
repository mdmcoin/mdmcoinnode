<h1 align="center"> 🚀️ MDMCOIN Blockchain Node</h1>

<p align="center">
  <a href="https://github.com/moedasdigitais/mdmcoin/actions" target="_blank">
    <img alt="Checks status" src="https://badgen.net/github/checks/mdmcoin/mdmcoinnode?cache=600"  />
  </a>
  <a href="https://github.com/mdmcoin/mdmcoinnode/releases" target="_blank">
    <img alt="Downloads" src="https://badgen.net/github/assets-dl/mdmcoin/mdmcoinnode?color=blue" />
  </a>

  <br/>



  <a href="https://t.me/mdmcoin" target="_blank">
    <img alt="Telegram" src="https://badgen.net/badge/icon/mdmcoin?icon=telegram&label=Telegram"/>
  </a>

</p>

> MDMCOIN is Based on WAVES an open source [blockchain protocol](https://waves.tech/waves-protocol). <br/> 
You can use it to build your own decentralized applications. Waves provides full blockchain ecosystem including smart contracts language called RIDE.



##  Getting started

A quick introduction of the minimal setup you need to get a running node. 

*Prerequisites:*
- configuration file for a needed network `mdm.conf`
- `mdm-all*.jar` file from [releases](https://github.com/mdmcoin/mdmcoinnode/releases) 

Linux systems:
```bash
sudo apt-get update
sudo apt-get install openjdk-8-jre
java -jar node/target/mdm-all*.jar path/to/config/mdm.conf
```

Mac systems (assuming already installed homebrew):
```bash
brew cask install adoptopenjdk/openjdk/adoptopenjdk8
java -jar node/target/mdm-all*.jar path/to/config/mdm.conf
```

Windows systems (assuming already installed OpenJDK 8):
```bash
java -jar node/target/mdm-all*.jar path/to/config/mdm.conf
```


> More details on how to install a node for different platforms you can [find in the documentation](https://docs.mdmcoin.com). 

## 🔧 Configuration

The best starting point to understand available configuration parameters is [this article](https://docs.mdmcoin.com).



Logging configuration with all available levels and parameters is described [here](https://docs.mdmcoin.com).

## 👨‍💻 Development

The node can be built and installed wherever Java can run. 
To build and test this project, you will have to follow these steps:

<details><summary><b>Show instructions</b></summary>

*1. Setup the environment.*
- Install Java for your platform:

```bash
sudo apt-get update
sudo apt-get install openjdk-8-jre                     # Ubuntu
# or
# brew cask install adoptopenjdk/openjdk/adoptopenjdk8 # Mac
```

- Install SBT (Scala Build Tool)

Please follow the SBT installation instructions depending on your platform ([Linux](https://www.scala-sbt.org/1.0/docs/Installing-sbt-on-Linux.html), [Mac](https://www.scala-sbt.org/1.0/docs/Installing-sbt-on-Mac.html), [Windows](https://www.scala-sbt.org/1.0/docs/Installing-sbt-on-Windows.html))

*2. Clone this repo*

```bash
git clone https://github.com/mdmcoin/mdmcoinnode.git
cd Waves
```

*3. Compile and run tests*

```bash
sbt checkPR
```

*4. Run integration tests (optional)*

Create a Docker image before you run any test: 
```bash
sbt node-it/docker
```

- Run all tests. You can increase or decrease number of parallel running tests by changing `waves.it.max-parallel-suites`
system property:
```bash
sbt -Dwaves.it.max-parallel-suites=1 node-it/test
```

- Run one test:
```bash
sbt node-it/testOnly *.TestClassName
# or 
# bash node-it/testOnly full.package.TestClassName
```

*5. Build packages* 

```bash
sbt packageAll                   # Mainnet
sbt -Dnetwork=testnet packageAll # Testnet
```

`sbt packageAll` ‌produces only `deb` package along with a fat `jar`. 

*6. Install DEB package*

`deb` package is located in target folder. You can replace '*' with actual package name:

```bash
sudo dpkg -i node/target/*.deb
```


*7. Run an extension project locally during development (optional)*

```bash
sbt "extension-module/run /path/to/configuration"
```

*8. Configure IntelliJ IDEA (optional)*

The majority of contributors to this project use IntelliJ IDEA for development, if you want to use it as well please follow these steps:

1. Click `Add configuration` (or `Edit configurations...`).
2. Click `+` to add a new configuration, choose `Application`.
3. Specify:
   - Main class: `com.wavesplatform.Application`
   - Program arguments: `/path/to/configuration`
   - Use classpath of module: `extension-module`
4. Click `OK`.
5. Run this configuration.

</details>

## 🤝 Contributing

If you'd like to contribute, please fork the repository and use a feature branch. Pull requests are warmly welcome.

For major changes, please open an issue first to discuss what you would like to change. Please make sure to update tests as appropriate.

Please follow the [code of conduct](./CODE_OF_CONDUCT.md) during communication with the each other. 

## ℹ️ Support (get help)


- [Telegram Dev Chat](https://t.me/mdmcoin)


## ⛓ Links

- [Documentation](https://docs.mdmcoin.com/)



## 📝 Licence

The code in this project is licensed under [MIT license](./LICENSE)

## 👏 Acknowledgements

[<img src="https://camo.githubusercontent.com/97fa03cac759a772255b93c64ab1c9f76a103681/68747470733a2f2f7777772e796f75726b69742e636f6d2f696d616765732f796b6c6f676f2e706e67">](https://www.yourkit.com/)

We use YourKit full-featured Java Profiler to make Waves node faster. YourKit, LLC is the creator of innovative and intelligent tools for profiling Java and .NET applications.

Take a look at YourKit's leading software products: YourKit Java Profiler and YourKit .NET Profiler.
