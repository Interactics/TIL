# 예외 처리



## Function-try-block
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
