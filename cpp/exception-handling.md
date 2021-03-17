# 예외 처리


# 예외 처리를 하는 이유
1. 코드의 가독성 향상을 위해.
주 목적은 코드의 주 흐름과 예외 처리를 분리시키는 목적이 크다. `if`문으로 처리 가능하지만, 해당 라인이 정보를 주로 처리하는 부분인지, 아니면 예외만을 처리하는 코드인지를 명확히 하기 어렵기 때문에 사용한다.


# 주의해야할 점.
- Stack Unwinding 작업 시에 이전의 해당 블록에서 만들어진 생성자는 파괴자를 호출하지 않는다. 따라서 Throw시 객체가 파괴자를 호출할 수 있는 별도의 코드가 필요하다.
- Throw 할 때에는  std::exception을 상속하여 던지는 게 유리하다. 해당 클래스를 상속하게 되면 다른 예외 클래스들을 이용할 수 있기 때문이다. -std::nested_exception 등등



# Function-try-block
보통 깔끔하게 보이게 하기 위해 사용한다.

    void f() try 
    { 
      ... 
    } catch (...)
    {
      ...
    }

위와 같은 형태로 쓰이며, 일반적으로 다음 2가지로 쓰인다.
1. 메인문 안에서 작은 기능을 수행할 때, 큰 예외처리가 필요 없는 경우 \


````
int main() try {
    // ...
    return 0;
} catch (...) {
// handle errors
  return -1;
}
````
    
2. 생성자를 사용할 때, 예외처리가 필요한 경우


```   
struct B {
  B() { /*might throw*/ }
};

struct A : B {
A() 
try : B() { 
   // ... 
} catch (...) {
   // handle exceptions thrown from inside A() or by B() 
} 
};
```
