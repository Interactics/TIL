# Template

# 함수 템플릿 
### 기본 포맷
    template <typename T>
    T Add(T a, T b){
        return a + b;
    }
- typename 대신 class 사용이 가능하다.


- 템플릿 함수는 컴파일 시에 함수를 생성한다.
- 따라서 소량의 컴파일 속도 저하가 발생한다.
  
# Specialization of Function Template
함수 템플릿의 특수화로, 어떤 type형에 대해서는 별도의 함수를 오버로딩하여 사용하는 방식을 일컫는다.

    template <typename T>
    T func(T a, T b){
        return a + b;
    }

    template<>
    char* func(char* a, char* b){
        return 0;
    }

    // 이는 아래 방법과 동이하다.

    template<>
    char* func<char*>(char* a, char* b){
        ...
    }

# Class Template

    template<typename T>
    class cls{
    private: 
        T a, b;
    public:
        cls(T x = 0, T y = 0) : a(x), b(y){ }
    }


    // 호출

    cls<double> test(10, 20);


## 외부선언 할 경우

    template<typename T>
    cls<T>::cls(T x, T y){
        ...
    }

- 템플릿은 컴파일 타임에 빌드 되어야하기 때문에 헤더 파일에 구현이 되어야한다.
- 하지만, .hpp 라는 확장자를 이용하면 선언과 구현을 분할 할 수 있다.


## 클래스 템플릿 특수화


    template <>
    class cls<char*>{
        ...
    }

### 부분 특수화
두 개 이상의 타입을 가진 클래스가 있을 때, 부분 형에 대한 특수화가 가능하다.

    template <>
    class cls<T, int>{
        ...
    }


## 템플릿 인자 
템플릿 매개변수는 아직 확정되지 않은 자료형을 지칭하는 이름으로 위에서는 T 혹은 T1이라 기술하였다.
이 템플릿 매개변수에 전달되는 자료형을 템플린 인자라 부른다.

    template<typename T, int a>
    class cls {
        ...
    }


### 디폴트 지정
템플릿의 매개변수도 디폴트 지정이 가능하다.

    temlpate<typename T = int, int a = 5>
    class cls{
        ...
    }

객체 생성에는 다음과 같다.

    cls<> test;


객체 생성할 때, 디폴트로 부르고자 한다면, <>를 반드시 추가하여 선언해야한다.



### template\<typename T> 와 template<>의 차이점

template\<typenmae t> 와 달리 template<>는 특수화처럼 자료형이 명확히 적혀있는 경우에 사용하면 된다.


    template <typename T>
    class SoSimple {
    public:
        T Simple(T a);
    }
    template <>
    class SoSimple<int>{
        int Simple(int a);
    }


## static
static 변수가 선언된 클래스는 그 자료형 마다 독립적인 클래스가 생성된다.
\<int> \<double>등 독립적인 static 을 보유하게 된다.
