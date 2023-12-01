# Test_ethereum_web3.js

## This is a code that Ethereum Web3.js Balance Checker (잔고 조회)

### web3.js를 사용하여 Ganache에서 제공되는 계정 목록을 가져와서 계좌의 잔고를 표시합니다.

----
<img src="https://img.shields.io/badge/Node.js-green?logo=Node.js&logoColor=black" alt="image" width="230" height="50"/>                     

v20.9.0


<img src="https://img.shields.io/badge/VS%20Code-blue?logo=visualstudiocode&logoColor=purple" alt="image2" width="230" height="50"/>         

v1.84.2


---
## !Description!
이 프로젝트는 Ethereum 블록체인의 가상 환경인 Ganache에서 제공되는 계정들 중에서 선택한 계정의 잔고를 확인하는 간단한 웹 어플리케이션입니다. 

Ethereum의 스마트 계약이나 dApp 개발 시 자주 사용되는 `web3.js` 라이브러리를 사용하였습니다.

---
This project is a simple web application that retrieves the balance of the selected account from the accounts provided by Ganache, a virtual environment for the Ethereum blockchain.
---

## Node.Js Code

### <index.js>
```
const Web3 = require('web3');

// Ganache의 RPC 서버 주소 (기본값은 http://127.0.0.1:7545)
const rpcServer = 'http://127.0.0.1:7545';

// Web3 인스턴스 생성
const web3 = new Web3(rpcServer);

// 계정 목록 가져오기
web3.eth.getAccounts().then(accounts => {
  if (accounts.length < 3) {
    console.error('계정이 충분하지 않습니다.');
    process.exit(1);
  }

  // 3번째 계정 주소
  const accountAddress = 0xa26227e25a0868DF41D17A4416366D0b42efAc49;    // (1000 ETH)
  
  // 계정의 잔고 가져오기
  web3.eth.getBalance(accountAddress).then(balance => {
    console.log(`계정 주소: ${accountAddress}`);
    console.log(`잔고: ${web3.utils.fromWei(balance, 'ether')} ETH`);
  }).catch(error => {
    console.error('잔고를 가져오는 중 오류 발생:', error);
  });
}).catch(error => {
  console.error('계정 목록을 가져오는 중 오류 발생:', error);
});

```


