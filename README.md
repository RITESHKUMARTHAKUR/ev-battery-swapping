<p align="center">
  <img src="https://img.icons8.com/?size=100&id=86079&format=png&color=#b0b8b5" width="100" />
</p>
<p align="center">
    <h1 align="center">EV-BATTERY-SWAPPING</h1>
</p>

<p align="center">
		<em>Developed with the software and tools below.</em>
</p>
<p align="center">
	<img src="https://img.shields.io/badge/GNU%20Bash-4EAA25.svg?style=flat&logo=GNU-Bash&logoColor=white" alt="GNU%20Bash">
	<img src="https://img.shields.io/badge/JavaScript-F7DF1E.svg?style=flat&logo=JavaScript&logoColor=black" alt="JavaScript">
	<img src="https://img.shields.io/badge/Prettier-F7B93E.svg?style=flat&logo=Prettier&logoColor=black" alt="Prettier">
	<img src="https://img.shields.io/badge/Grafana-F46800.svg?style=flat&logo=Grafana&logoColor=white" alt="Grafana">
	<img src="https://img.shields.io/badge/Prometheus-E6522C.svg?style=flat&logo=Prometheus&logoColor=white" alt="Prometheus">
	<img src="https://img.shields.io/badge/Redis-DC382D.svg?style=flat&logo=Redis&logoColor=white" alt="Redis">
	<img src="https://img.shields.io/badge/YAML-CB171E.svg?style=flat&logo=YAML&logoColor=white" alt="YAML">
	<img src="https://img.shields.io/badge/Jest-C21325.svg?style=flat&logo=Jest&logoColor=white" alt="Jest">
	<img src="https://img.shields.io/badge/Chai-A30701.svg?style=flat&logo=Chai&logoColor=white" alt="Chai">
	<img src="https://img.shields.io/badge/Mocha-8D6748.svg?style=flat&logo=Mocha&logoColor=white" alt="Mocha">
	<br>
	<img src="https://img.shields.io/badge/ESLint-4B32C3.svg?style=flat&logo=ESLint&logoColor=white" alt="ESLint">
	<img src="https://img.shields.io/badge/Passport-34E27A.svg?style=flat&logo=Passport&logoColor=white" alt="Passport">
	<img src="https://img.shields.io/badge/tsnode-3178C6.svg?style=flat&logo=ts-node&logoColor=white" alt="tsnode">
	<img src="https://img.shields.io/badge/TypeScript-3178C6.svg?style=flat&logo=TypeScript&logoColor=white" alt="TypeScript">
	<img src="https://img.shields.io/badge/Docker-2496ED.svg?style=flat&logo=Docker&logoColor=white" alt="Docker">
	<img src="https://img.shields.io/badge/Go-00ADD8.svg?style=flat&logo=Go&logoColor=white" alt="Go">
	<img src="https://img.shields.io/badge/Express-000000.svg?style=flat&logo=Express&logoColor=white" alt="Express">
	<img src="https://img.shields.io/badge/JSON-000000.svg?style=flat&logo=JSON&logoColor=white" alt="JSON">
</p>
<hr>
The EV Battery Swapping project aims to provide a seamless and efficient solution for electric vehicle (EV) battery swapping. By leveraging a combination of different programming languages and technologies, this project offers a robust platform for managing battery swaps, ensuring quick turnaround times and maximizing EV uptime.
<hr>

## Getting Started

***Requirements***

Ensure you have the following dependencies installed on your system:

* **NODEJS**: `v18.12.0 (LTS)`
* **Docker**: `v24.0.5`
* **GOLANG**: `go1.22.3`
###  Installation

1. Clone the ev-battery-swapping repository:

```sh
git clone https://github.com/RITESHKUMARTHAKUR/ev-battery-swapping.git
```

2. Change to the project directory:

```sh
cd ev-battery-swapping
```
###  Running ev-battery-swapping

Use the following command to run ev-battery-swapping: <br>
1 Start Network inside fabric-samples/test-network directory:
```sh
cd fabric-samples
cd test-network
./network.sh up
```
2. create channel
```sh
./network.sh createChannel
```
3. deploy chain code
```sh
./network.sh deployCC -ccn basic -ccp ../asset-transfer-basic/chaincode-javascript -ccl javascript
```
4. Export neccessary paths:
```sh
export FABRIC_CFG_PATH=$PWD/../config/
# Set environment variables for Org1
export CORE_PEER_TLS_ENABLED=true
export CORE_PEER_LOCALMSPID="Org1MSP"
export CORE_PEER_TLS_ROOTCERT_FILE=${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt
export CORE_PEER_MSPCONFIGPATH=${PWD}/organizations/peerOrganizations/org1.example.com/users/Admin@org1.example.com/msp
export CORE_PEER_ADDRESS=localhost:7051
```
5.Invoke Chaincode:
```sh
peer chaincode invoke -o localhost:7050 \
--ordererTLSHostnameOverride orderer.example.com \
--tls --cafile ${PWD}/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/tlscacerts/tlsca.example.com-cert.pem \
-C mychannel \
-n basic \
--peerAddresses localhost:7051 \
--tlsRootCertFiles ${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt \
--peerAddresses localhost:9051 \
--tlsRootCertFiles ${PWD}/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt -c '{"function":"InitLedger","Args":[]}'
```
6. Following should give some result
```sh
peer chaincode query -C mychannel -n basic -c '{"Args":["GetAllAssets"]}'
```
7. In `fabric-samples/asset-transfer-basic/rest-api-typescript`
```sh
npm install
npm run build
```
8. genrate env file
```sh
TEST_NETWORK_HOME=$HOME/fabric-samples/test-network npm run generateEnv
```
9.
`export REDIS_PASSWORD=$(uuidgen)`
```sh
npm run start:redis
```
	{If Error: docker: Error response from daemon: Conflict. The container name "/fabric-sample-redis" is already in use by container "1ec0e1b8bcc5d91d405f4fdbb6e47ae33101644e7c042419d65dd6245d70d5a9". You have to remove (or rename) that container to be able to reuse that name.

`e.g.`
  `9.1 run command: docker ps -a` 
	`9.2 search for container id with same as displayed in above error (ie. 1ec0e1b8bcc5)`
	`9.3 cmd :  docker rm 1ec0e1b8bcc5`

10.
```sh
npm run start:dev
```
11. sample api key
```sh
SAMPLE_APIKEY=$(grep ORG1_APIKEY .env | cut -d '=' -f 2-)
```
11.1 Copy value of sample api key
```sh
${SAMPLE_APIKEY}
```
11.2 open new terminal in fabric-frontend
```sh
cd fabric-frontend
npm install
```
11.3 paste value of Sample key in `home.js` file
```js
X-api-key = sample_apikey
```
11.4 in terminal of fabric-frontend
```sh
npm start
```
12.### Get all assets...
```shell
curl --header "X-Api-Key: ${SAMPLE_APIKEY}" http://localhost:3001/api/assets 
```
### Check whether an asset exists...

```shell
curl --include --header "X-Api-Key: ${SAMPLE_APIKEY}" --request OPTIONS http://localhost:3001/api/assets/asset7


### Create an asset...

```shell
curl --include --header "Content-Type: application/json" --header "X-Api-Key: ${SAMPLE_APIKEY}" --request POST --data '{"ID":"asset7","Manufacturer":"xyz","SOH":92,"Owner":"Jean","AppraisedValue":101}' http://localhost:3001/api/assets
```

### Read job status...

```shell
curl --header "X-Api-Key: ${SAMPLE_APIKEY}" http://localhost:3001/api/jobs/__job_id__
```

### Read transaction status...

```shell
curl --header "X-Api-Key: ${SAMPLE_APIKEY}" http://localhost:3001/api/transactions/__transaction_id__

### Read an asset...

```shell
curl --header "X-Api-Key: ${SAMPLE_APIKEY}" http://localhost:3001/api/assets/asset7
```

### Update an asset...

```shell
curl --include --header "Content-Type: application/json" --header "X-Api-Key: ${SAMPLE_APIKEY}" --request PUT --data '{"ID":"asset7","Manufacturer":"xyz","SOH":91,"Owner":"Jean","AppraisedValue":101}' http://localhost:3001/api/assets/asset7
```

### Transfer an asset...

```shell
curl --include --header "Content-Type: application/json" --header "X-Api-Key: ${SAMPLE_APIKEY}" --request PATCH --data '[{"op":"replace","path":"/Owner","value":"Ashleigh"}]' http://localhost:3001/api/assets/asset7
```

### Delete an asset...

```shell
curl --include --header "X-Api-Key: ${SAMPLE_APIKEY}" --request DELETE http://localhost:3001/api/assets/asset7
```

13. To close
`in test-network directory`
```sh
./network.sh down
```
##  Contributing
### Contributors

Thanks to these amazing contributors:

- [@RITESHKUMARTHAKUR](https://github.com/RITESHKUMARTHAKUR)
- [@Pranjal Hinduja](https://github.com/Pranjalhinduja)
- [@shubham-0927](https://github.com/shubham-0927)


Contributions are welcome! Here are several ways you can contribute:

- **[Submit Pull Requests](https://github.com/RITESHKUMARTHAKUR/ev-battery-swapping.git/blob/main/CONTRIBUTING.md)**: Review open PRs, and submit your own PRs.
- **[Join the Discussions](https://github.com/RITESHKUMARTHAKUR/ev-battery-swapping.git/discussions)**: Share your insights, provide feedback, or ask questions.
- **[Report Issues](https://github.com/RITESHKUMARTHAKUR/ev-battery-swapping.git/issues)**: Submit bugs found or log feature requests for Ev-battery-swapping.

<details closed>
    <summary>Contributing Guidelines</summary>

1. **Fork the Repository**: Start by forking the project repository to your GitHub account.
2. **Clone Locally**: Clone the forked repository to your local machine using a Git client.
   ```sh
   git clone https://github.com/RITESHKUMARTHAKUR/ev-battery-swapping.git
   ```
3. **Create a New Branch**: Always work on a new branch, giving it a descriptive name.
   ```sh
   git checkout -b new-feature-x
   ```
4. **Make Your Changes**: Develop and test your changes locally.
5. **Commit Your Changes**: Commit with a clear message describing your updates.
   ```sh
   git commit -m 'Implemented new feature x.'
   ```
6. **Push to GitHub**: Push the changes to your forked repository.
   ```sh
   git push origin new-feature-x
   ```
7. **Submit a Pull Request**: Create a PR against the original project repository. Clearly describe the changes and their motivations.

Once your PR is reviewed and approved, it will be merged into the main branch.

</details>

---





