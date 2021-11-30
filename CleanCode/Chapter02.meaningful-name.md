# 의미있는 이름

1. [의도를 분명히 밝혀라](#1.-의도를-분명히-밝혀라)
2. [그릇된 정보를 피하라](#2.-그릇된-정보를-피하라)
3. [의미 있게 구분하라](#3.-의미-있게-구분하라)

> 소프트웨어에서 이름은 어디나 쓰인다. 우리는 변수에도 이름을 붙이고, 함수에도 이름을 붙이고, 인수와 클래스와 패키지에도 이름을 붙인다. 소스파일은 물론 jar, war, ear 파일에도 이름을 붙인다. 이렇듯 많이 사용하므로 이름을 잘 지으면 여러모로 편하다. 이 장에서는 이름을 잘 짓는 간단한 규칙을 몇가지 소개한다.

### **1. 의도를 분명히 밝혀라**

"의도가 분명하게 이름을 지으라"고 말하기는 쉽다. 여기서는 의도가 분명한 이름이 정말로 중요하다는 사실을 거듭 강조한다.  
변수(혹은 함수나 클래스)의 존재 이유는? 수행 기능은? 사용 방법은? 따로 주석이 필요하다면 의도를 분명히 드러내지 못했다는 말이다.

```
int d; //경과 시간(단위: 날짜)
```

이름 d는 아무 의미도 드러나지 않는다. 경과 시간이나 날짜라는 느낌이 안든다. 측정하려는 값과 단위를 표현하는 이름이 필요하다.

```
int elapsedTimeInDays;
int daysSinceCreation;
int daySinceModification;
int fileAgeInDays;
```

의도가 드러나는 이름을 사용하면 코드 이해와 변경이 쉬워진다.

```
public List<int[]> getThem(){
  List<int[]> list1 = new ArrayList<int[]>();
  for(int[] x:theList)
    if(x[0] == 4)
      list1.add(x);
  return list1;
}
```

위의 경우, 코드가 하는 일을 짐작하기 어렵다. 문제는 코드의 단순성이 아니라 코드의 함축성이다. 코드 맥락이 코드 자체에 명시적으로 드러나지 않는다.

```
public List<int[]> getFlaggedCells(){
  List<int[]> flaggedCells = new ArrayList<int[]>();
  for(int[] cell:gameBoard)
    if(cell[STATUS_VALUE] == FLAGGED)
      flaggedCells.add(cell);
  return flaggedCells;
}
```

코드의 단순성은 변하지 않았다. 단순히 이름만 고쳤는데도 함수가 하는 일을 이해하기 쉬워졌다.

### **2. 그릇된 정보를 피하라**

프로그래머는 코드에 그릇된 단서를 남겨서는 안 된다. 그릇된 단서는 코드 의미를 흐린다. 나름대로 널리 쓰이는 의미가 있는 단어를 다른의미로 사용해도 안 된다.

예를 들어, 여러계정을 그룹으로 묶을 때, 실제 List가 아니라면 accountList라 명명하지 않는다. 프로그래머에게 List라는 단어는 특수한 의미다. acoountGroup, bunchOfAccounts, 아니면 단순히 Accounts라 명명한다.

서로 흡사한 이름을 사용하지 않도록 주의한다. 한 모듈에서 XYZControllerForEfficientHandlingOfStrings라는 이름을 사용하고, 조금 떨어진 모듈에서 XYZControllerForEfficientStorageOfStrings라는 이름을 사용한다면?

유사한 개념은 유사한 표기법을 사용한다.일관성이 떨어지는 표기법은 그릇된 정보다.

이름으로 그릇된 정보를 제공하는 진짜 끔찍한 예가 소문자 L 이나 대문자 O변수다.

```
int a = l;
if (O == l)
a = Ol;
else
l = 01;
```

소문자 L은 숫자 1처럼 보이고 대문자 O는 숫자 0처럼 보인다.

### **3. 의미 있게 구분하라**
