# Stack 배열 구현

## 스택의 기능

- INIT

- FULL

- EMPTY

- PUSH

- POP

- PEEK

- PRINT

  ------

```c
//스택 초기화
void init(Stack * p) {
	p->top = 0;
}

//스택이 가득차있는지 확인
int full(Stack* p) {
	if (p->top == MAX - 1) return 1;
	else return 0;
}

//스택이 비었는지 확인
int empty(Stack * p) {
	if (p->top == 0) return 1;
	else return 0;
}

//스택에 데이터 추가
void push(Stack * p, element x) {
	if (full(p)) {
		printf("현재 스택 용량이 가득찼습니다.\\n");
	}
	else {
		p->top += 1;
		p->stack[p->top] = x;
	}
}

//스택 제일 위에 있는 데이터 반환 후 제거
element pop(Stack * p) {
	element e;
	if (empty(p)) {
		printf("현재 스택이 비어있습니다.\\n");
		exit(1);
	}
	else {
		e = p->stack[p->top];
		p->top -= 1;
		return e;
	}
}

//스택 제일 위의 데이터 반환
element peek(Stack * p)
{
	if (empty(p)) {
		printf("현재 스택이 비어있습니다.\\n");
		exit(1);
	}
	else {
		return p->stack[p->top];
	}
}

//현재 스택 현황 출력
void print(Stack* p) {
	int i;
	printf("현재 스택 현황: ");
	for (i = 1; i <= p->top; i++)
		printf("%d ", p->stack[i]);
	printf("\\n");
}
// 스택 삽입 함수
void push(int data) {
    if (top == SIZE - 1) // 만약 top의 인덱스가 9999를 넘는다면 더 이상 데이터가 들어갈 수 가 없으므로 에러 메시지가 뜸.
    {
        printf("스택오버플로우가 발생했습니다. \\n");
        return;
    }
    stack[++top] = data;
}

// 데이터 추출 함수
int pop() {
    if (top == -1) // 만약 top이 -1이면 스택의 원소가 하나도 없다는 의미이다.
    {
        printf("스택언더플로우가 발생했습니다. \\n");
        return -INF;
    }
    return stack[top--];
}
```

- 스택오버플로우: 스택 메모리가 지정된 범위를 넘어 갈 때 발생함.
- 스택언더플로우: 스택에서 데이터를 삭제 하려 할때, 스택에 데이터가 없는 상태에서 삭제를 시도하면 발생하는 오류.