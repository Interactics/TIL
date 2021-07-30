# STL


# Container



## Vector

- 메모리를 자동적으로 할당해주는 배열이다.
- 벡터를 생성하면 메모리 heap에 동적할당으로 생성한다. 
- <vector> 헤더를 추가하여 사용한다.
- ``std::vector<data type> name`` 형식으로 사용가능하다.

### 특징 
- 동적으로 원소를 추가할 수 있으며, 자동으로 크기가 변경된다.
- 속도 측면에서 배열에 비해 속도가 떨어진다. 
- 원소가 추가되거나 삽입할 때, 메모리 재할당이 발생가능하다. 이때 부하가 발생할 한다.
- capacity가 모자를 경우, cap /2 만큼의 크기를 계속 늘려간다. 


### 이터레이터
- 포인터의 일종. STL 컨테이너의 데이터를 가리킨다.
- begin() 메서드는 시작 주소르 리턴, end() 메서드는 끝 주소를 리턴한다. 
  - 이때 end()는 끝 다음 주소를 리턴하는데, 이터레이터가 여기에 도달하면 모든 값을 도달한 것이다.
- `vector<자료형>::iterator 이터레이터명`을 선언가능하다만, `auto`르 써도 무방.
- 증감연산 가능하다. 가능 여부는 컨테이너마다 다르다. 
- 사용하는 이유는 STL에 통일된 포인터 개념도입을 위함이다.
- 

### size와 capacity
- size는 할당된 메모리 안에 들어있는 요소의 갯수
- capacity는 할당된 메모리의 크기이다. 

### 사용법

```
std::vector<int> v; // 벡터 v 생성
std::vector<int> v(5) // 0으로 초기화된 원소 5개 생성한다.
std::vector<int> v(5, 2) // 2로 초기화된 원소 5개를 생성한다.
std::vecotr<int> v(w) // w 벡터르 복사하여 v로 생성한다.
```


### 메서드
```
std::vecotr<int> v;
v.assign(5,2); // 5개 원소 생성 후 전원 2로 초기화
v.at(i); // i번째 원소르 참조한다. 
v[i]; // i번째 원소를 참조한다.
// v[i]는 빠르다. 다만 범위 점검 안함.
// v.at(i)는 범위점검이 있어 안전하다.

v.front() // 첫번째 원소를 참조한다.
v.back() // 마지막 원소르 참조한다.
v.clear() // 모든 원소를 제거한다. 메모리는 그대로 유지한다. 

v.push_back(7); // 벡터 배열의 끝에 7을 삽입한다.
v.pop_back(); // 마지막 원소를 제거한다.

v.begin(); // iter 첫번째 원소를 가리킨다.
v.end(); // iter 마지막의 다음을 가리킨다.

v.rbegin(); // reverse begin
v.rend();   // reverse end

v.reserve(n); // n개의 원소를 저장할 위치를 동적할당으로 예약한다. - 즉 capacity를 늘린다.
v.resize(n); // 크기를 n로 변경하고, 크기가 커졌을 경우 추가된 값은 0으로 초기화한다.
v.resize(n,3); // 크기를 n로 변경하고 크기가 커졌다면 3으로 초기화한다.

v.size();  // 원소 갯수 리턴
v.capacity(); // 할당된 공간의 크기를 리턴
v2.swap(v1); // v1과 v2 원소의 capacity를 바꾼다. 

v.insert(2, 3, 4); // 2번째 위치에 3개의 4를 삽입한다.
v.insert(2, 3);    // 2번째 위치에 3을 삽입한다. 삽입 후 iterator를 반환한다.
v.erase(iter); // iter가 가리키는 원소르 제거한다. 사이즈는 줄어들고 메모리는 유지한다.

v.empty(); // 비어있다면, size의 크기 == 0 이면 true


#smart pointer

## unique_ptr
  - 포인터 공유하지 않음.
  - 유일한 소유권
  
  - double free 버그 : 소멸된 객체를 다시 소멸 시키는 버그 
  - 더브 프리 버그를 없애기 위해 unique 포인터가 생김
  
  
  ```
  std::unique_ptr<A> pa(new A());
  // A* pa = new A(); 와 유사
  ```
  - 복사 생성자를 삭제했기 때문에, 클래스으 복사가 진행되지 않음.
  
  소유권 이전하기
  ```
  std::unique_ptr<A> pa(new A());
  
  std::unique_ptr<A> pb = std::move(pa);
  ```
  - 이 이후 pa 는 아무것도 지칭하지 않음. 
  - pa.get() 으 주소값 확인시 nullptr을 지정함.
  - 따라서 pa 는 댕글리 포인터가 되어 참조 시 에러 발생함. 주의
  
  ### 함수 인자로 unique_ptr 사용하기
  ```
  void do(std::unique_ptr<A>& ptr) {ptr -> doo(1);) // 객체 소유권이 함수 인자인 ptr로 넘어가므로 원칙 위배
  
  void do(A* ptr) {ptr -> doo(1);} // ptr로 바로 사용하도록하기
  ```
  
  
  


