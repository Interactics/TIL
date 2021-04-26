# Golang

# 기본

'''
package main

import "fmt"

func add(a int, b int) (result int){
    result = a + b;
} // naked return

func mult(a int, b int) int {
    result := a * b;
    
    return result
} // 일반 형태

func main() {
	fmt.Println("Hello world")
}
'''

# 기타 특징

- 포인터가 존재. 주소 값에 접근할 수 있다. 
- 다른 언어들과 달리 클래스가 존재하지 않음. struct에 함수를 넣어 메서드처럼 사용함.
- 'defer' 라는 함수로 함수가 종료된 후 동작을 하게 하는 기능이 있음. 
- naked return이라 하여 함수의 머리 부분에 리턴형을 표기하는 방식이 존재.
- ':=' 와 '=' 의 차이. auto 와 := 는 동일. 자동으로 형을 맞추어준다. 다만 함수 안에서만 사용할 수 있음. 전역으로 사용이 불가능.
- 사용하지 않는 변수는 지워야한다. 지우지 않으면 빌드 시에 에러난다.

