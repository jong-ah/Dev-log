# CI/CD

시장과 고객의 요구에 빠르게 반응해서 제품을 출시, 업데이트하는 것이 중요합니다. 그렇기 때문에 많은 회사들이 **어플리케이션 개발 단계부터 배포 때까지 이 모든 단계들을 자동화하여 효율적이고 빠르게 배포할 수 있도록 만든 개발 프로세스 CI/CD**를 사용합니다.

### CI

- Continuous Integration 지속적인 통합의 약자
  - 코드 변경사항을 주기적으로 빈번하게 머지
  - 통합을 위한 단계 (빌드, 테스트, 머지)의 자동화
- 팀에서 만든 CI Server Script를 통해 결과를 확인할 수 있습니다.
- 장점 : 개발 생산성 향상, 문제점을 빠르게 발견, 버그 수정 용이, 코드의 퀄리티 향상

<br>

### CD

- Continuous Delivery 지속적인 제공의 약자 or Continuous Deployment 지속적인 배포의 약자 
  - CI를 통해서 자동으로 빌드, 테스트가 되었다면 배포 준비를 완료한다.
  - [Delivery] 최종 배포 전에 수동적으로 '배포에 문제가 없는지' 개발자나 검증팀이 검토하고 배포한다.
  - [Deployment] 수동적으로가 아닌 자동적으로 배포한다면 지속적인 배포할 수 있다.
- 회사마다 팀마다 다른 방식으로 적용할 수 있고, CI를 거쳐서 CD를 진행하기 때문에 둘이 묶어서 CI/CD라고 말합니다.

<br>

### CI/CD 파이프라인

1. **Code** : 개발자가 작은 단위로 기능을 나누어서 주기적으로 메인 레포지토리에 머지합니다.
2. **Build** : 자동으로 빌드합니다.
3. **Test** : 테스트 과정을 거칩니다. (결과 알림)
4. **Release** : 배포 준비를 합니다.
5. **Deploy** : 수동적으로 또는 자동으로 최종 배포합니다.

CI/CD 툴로는 Jenkins, Buildkite, Github Actions 등이 있습니다.

<br>

### 참고자료

- [CI/CD 5분 개념 정리 (현업에서 쓰는 개발 프로세스)](https://youtu.be/0Emq5FypiMM)
- [CI/CD 자동화가 가져다 준 행복 in LINE Engineering](https://engineering.linecorp.com/ko/blog/ci-cd-automation/)
- [CI&CD with FrontEnd developer in Vingle Tech Blog](https://medium.com/vingle-tech-blog/ci-cd-with-frontend-developer-c8aed9ca06c0)
