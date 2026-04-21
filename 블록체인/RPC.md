# RPC(Remote Procedure Call)
 - 블록체인에서 `RPC`는 블록체인 노드과 `DApp` 사이의 통신하는 역할을 합니다.
 - 블록체인 네트워크에서 특정 지갑 잔액 조회나 트랜잭션 전송, 블록 데이터 조회, 스마트 컨트랙트를 호출합니다.

사용자들은 보통 직접 블록체인 노드를 띄우지 않기 때문에 `Infura`나 `Alchemy` 같은 `RPC 업체`들을 통해서 API 형태로 블록체인 네크워크와 통신하게 됩니다. 만약 `RPC 업체`를 사용하지 않는다면 사용자가 직접 블록체인에 노드를 띄운 후, 해당 노드의 `RPC` 기능을 사용해야 합니다.

직접 블록체인에 노드를 띄우는 방식 보다는 `RPC 업체`를 통해 통신하는 것이 비용 및 호율 측면에서 뛰어납니다.
`이더리움` 네트워크에서는 `JSON-RPC`를 사용합니다.
## 사용 예
### 지갑 잔액 조회 기능 
### 흐름
`내 앱/지갑` -> `RPC 서버에 지갑 잔액 조회 요청` -> `이더리움 노드가 블록체인 조회`  -> `result 반환`
#### 요청
```json
{
	"jsonrpc": "2.0",  // 통신 규격 버전
	"method": "eth_getBalance",
	"params": ["0xYourWalletAddress", "latest"],  // 조회할 지갑 주소와 최신 블록 기준
	"id": 1
}
```
#### 응답
```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": "0x1bc16d674ec80000"  // 0.1 ETH(16진수 Wei 단위 금액)
}
```
## 참고 자료
- https://travel-with.tistory.com/entry/blockchainrpc
- https://www.linkedin.com/pulse/rpc-nodes-blockchain-payment-gateways-ossystem-7cw6e/