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


