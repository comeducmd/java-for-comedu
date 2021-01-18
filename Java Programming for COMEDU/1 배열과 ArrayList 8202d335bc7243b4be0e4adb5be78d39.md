# 1. 배열과 ArrayList

# 배열

---

[다른 자료형과 비교하기](https://www.notion.so/0-8558590bad4a48dbac36dc791cce4add)

배열은 같은 타입의 변수들로 이루어진 유한한 크기의 자료구조이다.

배열의 길이는 고정되어 있다.

### 1) 배열을 써야하는 이유

동일한 자료형의 변수를 한꺼번에 순차적으로 관리할 수 있다.

### 2) 배열 선언

- `자료형[] 배열이름 = new 자료형[길이];`
- `자료형 배열이름[] = new 자료형[길이];`

```java
int[] arr1 = new int[10];
int[] arr2 = new int[10];
int[] arr3 = new int[];  //길이 값을 입력하지 않아 오류가 발생한다

int[] arr4;
arr4 = new int[3]; //따로따로 생성할 수 있다.

```

### 3) 배열 초기화

- 배열을 초기화할때는 배열의 길이를 명시하지 않는다

```java
int[] nums1 = new int[] {1,2,3}  //옳은 초기화
int[] nums2 = new int[3] {1,2,3} // 옳지 않은 초기화
```

- 초기화하지 않고 선언한 경우,
    - 정수는 0
    - 실수는 0.0
    - 객체 배열은 null로 초기화 된다.

### 4) 배열 접근

배열의 값은 인덱싱을 활용해 접근한다.

배열의 인덱스는 0부터 시작하며, 길이가 n인 배열은 인덱스가 0부터 n-1까지 존재한다.

```java
String[] OOP = new String[] {"윤세린", "최지원", "김준영", "정유찬"};

OOP[0] = "윤세린";
OOP[1] = "최지원";
OOP[2] = "김준영";
OOP[3] = "정유찬";
```

💡 배열의 길이는 `배열.length` 를 사용해 구한다.

### 5) 배열 주요 메소드

- **배열의 길이 구하기**

    `length`

- **배열 복사하기**

    `System.arraycopy(COPY, COPYPOS,PASTE, PASTEPOS,LENGTH)` 

    `COPY` : 복사할 배열 이름

    `COPYPOS` : 복사할 배열의 첫번째 위치

    `PASTE` : 붙여넣을 배열 이름

    `PASTEPOS` : 붙여넣을 배열의 붙여넣기 시작할 첫번째 위치

    `LENGTH` : 복사 붙여넣기할 요소의 개수

    ```java
    int[] arr1 = {2, 3, 4, 5, 6};
    int[] arr2 = new int[8];

    System.arraycopy(arr1, 0, arr2, 3, 3);
    ```

    ```java
    //RESULT :
    arr1 = {2, 3, 4, 5, 6};
    arr2 = {0, 0, 0, 2, 3, 4, 0, 0};
    ```

- **응용 for문**

    `for (iterator : array) { 반복 실행문; }` 

    ```java
    int[] arr = {2, 3, 4, 5, 6};

    for (int i : arr) { System.out.println(i);}
    ```

    ```java
    //RESULT
    2
    3
    4
    5
    6
    ```

## 객체 배열

---

참조 자료형을 선언하는 객체 배열인다.

이때 배열만 선언한 경우 null로 초기화 된다.

### 객체 배열 복사하기

1. **얕은 복사**

    배열의 주소만 복사되므로 배열 요소가 변경된 배열의 값도 변경됨

    ```java
    Student[] arr1 = new Student[4];
    Student[] arr2 = new Student[4];

    arr1[0] = new Student("윤세린", 22);
    arr1[1] = new Student("최지원", 21);
    arr1[2] = new Student("김준영", 22);
    arr1[3] = new Student("정유찬", 22);

    System.arraycopy(arr1, 0, arr2, 0, 4);

    //arr1을 arr2에 복사.
    //이때의 복사는 얕은 복사이므로 배열의 주소가 복사된다.
    //따라서 arr1[i]와 arr2[i]의 객체는 같은 주소값을 가르키고 있다.

    arr1[1].setage(19);

    System.out.println(arr1[1].name + arr1[1].age);
    System.out.println(arr2[1].name + arr2[1].age);
    ```

    ```java
    //RESULT

    최지원 19
    최지원 19

    //arr1에서 객체의 property를 수정하면, arr2에서도 수정이 일어난다.
    ```

2. **깊은 복사**

    서로 다른 인스턴스의 메모리를 요소로 가지게 됨

    ```java
    Student[] arr1 = new Student[4];
    Student[] arr2 = new Student[4];

    Student[0] = new Student("윤세린", 22);
    Student[1] = new Student("최지원", 21);
    Student[2] = new Student("김준영", 22);
    Student[3] = new Student("정유찬", 22);

    for (int i=0; i < arr1.length; i++){
    	arr2[i] = new Student(arr1[i].name, arr1[i].age);
    }

    //arr1을 arr2에 복사.
    //이때의 복사는 깊은 복사이므로 두 객체는 다른 주소값을 가르키고 있다.
    //따라서 arr1[i]와 arr2[i]의 객체는 다른 주소값을 가르키고 있다.

    arr1[1].setage(23);

    System.out.println(arr1[1].name + arr1[1].age);
    System.out.println(arr2[1].name + arr2[1].age);
    ```

    ```java
    //RESULT

    최지원 23
    최지원 21

    //arr1에서 객체의 property를 수정하면, arr2에서도 수정이 일어나지 않는다.
    ```

## 다차원 배열

---

2차원 이상의 배열이다.

n차원의 배열은 1차원 배열이 n개 있다고 생각할 수 있다.

### 다차원 배열의 선언과 초기화

- **이차원**

    선언

    `자료형[ ][ ] 배열 이름 = new 자료형 [ 길이1 ][ 길이2 ]`

    초기화

    `자료형[ ][ ] 배열 이름 = { {1, 2, 3}, { 4, 5, 6} };`

    ![1%20%E1%84%87%E1%85%A2%E1%84%8B%E1%85%A7%E1%86%AF%E1%84%80%E1%85%AA%20ArrayList%208202d335bc7243b4be0e4adb5be78d39/Untitled.png](1%20%E1%84%87%E1%85%A2%E1%84%8B%E1%85%A7%E1%86%AF%E1%84%80%E1%85%AA%20ArrayList%208202d335bc7243b4be0e4adb5be78d39/Untitled.png)

- **이차원 이상**

    직접 응용해보자.

# ArrayList

---

[다른 자료형과 비교하기](https://www.notion.so/0-8558590bad4a48dbac36dc791cce4add)

ArrayList는 List 인터페이스를 상속받은 클래스로 크기가 가변적으로 변하는 선형 리스트이다.

JDK 5.0부터 자료형의 안정성을 위헤 제너릭스(Generics)라는 개념이 도입되었다.

### 0) 제너릭스(Generics)

ArrayList에는 다양한 객체를 담을 수 있지만 보통 한 종류의 객체를 담는 경우가 더 많다.

이때 제너릭스를 사용하지 않으면 ArrayList 안에 모두 object로 들어가기 때문에 매번 형변환을 해줘야 한다.

제너릭스는 다룰 객체를 미리 명시함으로서 타입 안정성을 제공해주고 타입체크와 형변환을 대신 해결해주는 자바의 기능이다.

```java
Arraylist <Integer> numarray = new ArrayList <Integer>();
```

💡 제너릭스는 객체 타입만 선언할 수 있다.

따라서 primitive 자료형인 int와 string 등은 Wrapper 클래스인 Integer나 String을 사용해 선언해야 한다.

### 1) ArrayList를 사용해야 하는 이유

기존의 배열은 길이가 정해져 있으므로 크기가 부족한 경우 더 큰 배열로 복사해야 한다.

ArrayList는 배열과 비슷한 자바의 자료형으로, 동적으로 크기가 변해 이러한 배열의 단점을 극복할 수 있다.

또한, 자바에서 다양한 메서드와 속성을 제공해 객체 배열을 편리하게 관리할 수 있다.

### 2) ArrayList 주요 메서드

- **배열에 요소 추가**

    `add (value)` 

    `add(index, value)`

    ```java
    ArrayList<String> days = new ArrayList<String>[7];

    days[0] = "주말"; //ArrayList는 인덱스를 사용하지 않는다.
    days.add("주말");
    days.add(0, "주중");
    ```

- **배열에 추가된 요소 개수 반환**

    `size()`

- **배열의 index 위치에 있는 요소 값 반환**

    `get(index)`

    ```java
    String day = days.get(0);
    ```

- **배열의 요소 값 제거**

    `remove(value)`

    `remove(index)`

    ```java
    days.remove("주중");  //True 리턴
    days.remove(0);      //삭제된 값 리턴
    ```

- **배열이 비어 있는지 확인**

    `isEmpty()`

---

작성자 | 김준영
참고자료 | Do it! 자바 프로그래밍 입문