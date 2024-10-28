# java-racingcar-precourse

## 요구사항
1. 각 자동차는 이름을 가진다.
   - 자동차 이름을 입력 받을 때 각 자동차의 이름은 쉼표로 구분한다.
   - 입력에서 이름 맨 처음이나 맨 끝에 있는 공백은 삭제한다.
   - 이름은 삭제한 공백 제외 5자 이하이다.
2. 주어진 횟수 동안 각 자동차는 전진하거나 전진하지 않는다.
   - 사용자가 몇 번의 이동을 할 것인지를 자연수로 입력한다.
   - 횟수는 최대 10회로 제한한다.
   - 각 자동차 별로 0에서 9까지의 무작위 값을 구한 후 4 이상이면 전진한다.
3. 각 시도가 끝나고 실행 결과를 출력한다.
   - 자동차 이름과 진행 상황을 함께 출력한다.
4. 완료한 후 최종 우승자를 출력한다.
   - 우승자는 한 명 이상이다.
   - 우승자가 여러 명일 경우 쉼표로 구분하여 출력한다.
5. 사용자가 잘못된 값을 입력할 경우 IllegalArgumentException을 발생시킨 후 애플리케이션을 종료한다.

### 예외 상황
-  이름이 6자 이상이면 예외
- 입력값 시작이나 끝이 쉼표이면 예외
- 이름이 중복되면 예외
- 이름이 비었으면 예외
- 입력이 비었으면 예외
- 시도 횟수 입력값이 자연수가 아니면 예외
- 10이 넘으면 예외
- 입력이 비었으면 예외

## 기능 구현 목록
1. 입력 받기
- 자동차 이름을 입력 받는다.
- 콤마로 나누고 공백 처리 한 후 리스트에 저장한다.
- 자동차 이름 예외 처리 한다.
- 시도할 횟수를 입력 받는다.
- 시도 횟수 예외 처리 한다.
2. 레이싱
- 각 자동차의 [이름, 전진 횟수]를 저장한 리스트를 만든다.
- 각 자동차 별로 0~9 중 랜덤값을 추출하여 4 이상이면 전진 횟수를 1 높인다.
- 진행 상황을 출력한다.
- 시도 횟수만큼 반복한다.
3. 우승자 찾기
- 가장 많이 전진한 자동차들을 찾아 리스트에 저장한다.
- 쉼표로 구분하여 출력한다.

## 구조 설계
- controller.RacingController
  - 메인 실행 메소드 racing
- service.RacingService
  - 입력값 처리 setCarsAndRoundNumber
  - 자동차 입력값 처리 setCars
  - 자동차 이름 추출 splitCars
  - 자동차 이름 검증 validateCarsInput
  - 자동차 이름 길이 확인 checkCarsLength
  - 자동차 이름 중복 확인 checkCarsDuplication
  - 횟수 입력값 처리 setRoundNumber
  - 횟수 검증 validateRoundNumberInput
  - 전진 횟수 리스트 생성 initializeCarsStatus
  - 횟수만큼 반복 메인 메소드 racing
  - 차 별 전진/멈춤 메소드 moveCars
  - 랜덤값 뽑기 getRandomValue
  - 우승자 찾기 findWinner
- view.InputView
  - 자동차 이름 입력 inputCars
  - 시도 횟수 입력 inputRoundNumber
- view.OutputView
  - 라운드별 실행 결과 출력 printRoundResult
  - 최종 우승자 출력 printWinners