# 하이퍼레저 패브릭 기반 투표 앱 for 팬(Make for fan)

<img src="./images/fff.png" width="65%">
</br>

## 프로젝트 명
### 블록체인 기반 투표 앱 for 팬
</br>

## 프로젝트 팀
### 박찬형(팀장) | 김명석 | 원소희 | 최한솔
</br>

## 프로젝트 기간
### 19.11.26 ~ ing
</br>

# 프로젝트 목표(개요)
최근 서바이벌 오디션 프로그램이 폭발적인 인기를 끌었습니다.  
시청자는 국민 프로듀서가 되어 자신이 좋아하는 연습생에게 표를 행사하고 투표한 결과에 따라 연습생들이 그룹을 이루어 데뷔하게 되는데,  
이렇게 데뷔한 그룹들은 차세대 `K-POP` 인기의 주역이 되었습니다.
</br>

하지만, 얼마 전 `100%` `국민 프로듀서`의 투표로만 데뷔 멤버가 정해진다는 방송국 측의 말과 달리 내부자가 투표에 관여해 결과를 조작했다는 사실이 발각되었습니다.  
이에 따라 해당 오디션 프로그램으로 데뷔하게 된 연습생들이 더이상 방송 활동을 하지 못하게 조치가 취해졌고 있고,  
분노한 시청자들은 제작진에게 책임을 묻고 있습니다.
</br>

이러한 문제를 보면서,  
저희는 팬들에게 `Hyperledger Fabric`을 이용해 투명한 `K-POP` 투표 시스템을 제공하고자 합니다.  
내부자의 조작이 불가능한 모델로,  
투표에 참여하는 기관들이 합의 하에 투표 데이터를 저장하도록 해 투표한 모든 사람이 투표 결과를 신뢰할 수 있도록 합니다.  
나아가 `K-POP` 팬들에게 혜택이 돌아가는 서비스를 제공합니다.  
</br></br>

# 개발 언어 환경 | 구성 환경
<img src="./images/fff-project-config.png">
</br>

| BlockChain | API Server | Applicationc|
|:----------:|:----------:|:----------:|
|Hyperledger Fabric | Node.js | React.js |

</br></br>

<h4>

- `Hyperledger Fabric` 네트워크를 작성하고, 네트워크에 `Smart Contract(Chaincode)`를 설치하고 인스턴스화합니다.
- `Node.js` 서버는 `Fabric SDK`를 사용하여 `Hyperledger Fabric` 네트워크와 상호작용하고, `Web/App` 클라이언트용 `API`를 작성합니다.
- `React.js` 클라이언트는 `Node.js` 애플리케이션 `API`를 사용하여 네트워크와 상호작용합니다.
- 사용자는 `React.js` 웹/앱 인터페이스와 상호작용하여 투표하고, 현재 상태를 조회하기 위해 `World State`를 쿼리합니다.

</h4>
</br></br>

# How to demonstration

## 지금 실행 중인 서버에 접근하려면 아래 링크에 접속해주세요.<br>
[Demo](http://ch-4ml.iptime.org:3000)

## 직접 구축해보려면 아래를 따라 진행해주세요.
링크를 따라 실행 환경 구축을 먼저 완료해주세요.
[실행 환경 구축 방법](https://github.com/ch-4ml/Hyperledger-Configuration/blob/master/ubuntu_setup/ChangeConfig.md)

환경 구축을 완료하셨다면, Docker를 이용해서 네트워크를 구축하고, 체인코드를 Peer에 설치 후 채널에 배포해야 합니다.
현재, 간단히 실행할 수 있도록 Shell Script로 실행 명령이 자동화되어 있습니다.
```shell
$ cd make-for-fan/network
$ ./generate.sh
$ ./start.sh
$ ./cc.sh
```

모든 과정을 이상 없이 수행하셨다면, 서버에 Hyperledger-Fabric Network가 가동되고 있는 상태입니다.
이제 어플리케이션을 실행해봅시다.
지금부터는 React 환경을 실행하기 위한 Client용 Terminal과 Node.js API Server를 실행하기 위한 Server용 Termial이 필요합니다.
Terminal 2개를 실행해주세요.
```shell
# Terminal 1
$ cd make-for-fan/application

# Terminal 2
$ cd make-for-fan/application/front
```

어플리케이션을 실행하기 전, Hyperledger Fabric 네트워크의 이용 권한을 가진 Admin Wallet을 생성해야 합니다.
```shell
# Terminal 1
$ node ./enrollAdmin.js
```

정상적으로 실행되면, 'wallet'이라는 이름을 가진 새로운 디렉토리가 생성되고, 아래에 Admin Wallet의 정보가 생성됩니다.
이제 어플리케이션을 이용할 수 있습니다.
```shell
# Terminal 1
$ node ./server-local.js

# Terminal 2
$ npm start
```

React.js 클라이언트는 현재 localhost:3000에서 작동합니다. 접속해서 실행해주세요!
