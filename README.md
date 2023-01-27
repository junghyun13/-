# c
 1부터 n까지의 수를 스택에 넣었다가 뽑아 늘어놓음으로써, 하나의 수열을 만들 수 있다. 이때, 스택에 push하는 순서는 반드시 오름차순을 지키도록 한다고 하자. 임의의 수열이 주어졌을 때 스택을 이용해 그 수열을 만들 수 있는지 없는지, 있다면 어떤 순서로 push와 pop 연산을 수행해야 하는지를 알아낼 수 있다. 이를 계산하는 프로그램을 작성하라.
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int stack[100];
// 스택 (stack)은 기본적인 자료구조 중 하나로, 컴퓨터 프로그램을 작성할 때 자주 이용되는 개념이다. 스택은 자료를 넣는 (push) 입구와 자료를 뽑는 (pop) 입구가 같아 제일 나중에 들어간 자료가 제일 먼저 나오는 (LIFO, Last in First out) 특성을 가지고 있다.
int top=-1;


int empty(){
	if(top<0)
	  return 1;
	else
	  return 0;
}


void push(int v){
	stack[++top]=v;
}


int pop(){
	if(empty() == 1)
	  return 'fail';
	else
	  return stack[top--];
}


int main(){
	int n,i,answer,j,count,r;
	char *result;
	printf("총 입력할 숫자의 개수는? ");
	scanf("%d",&n);
	result=(char*)malloc(sizeof(char)*(n*2+1));
	j=1;
	count=0;
	
	for(i=0;i<n;i++){
	    printf("숫자를 입력해주세요: \n");
	    scanf("%d",&answer);
	    while(j <= answer){
	    	push(j);  //answer의 값보다 크기전까지 계속 스택에 값을 넣어나간다  
	    	result[count++]='+'; j++;}
		r=pop(); //answer값과 j값에서 서로 같은 부분을 pop처리 한다  
		
		if(r == answer){
			result[count++]='-';  }
		
		
		else{
			printf("NO\n");
			free(result);
			return 0;}
    }
    
    for(i=0;i<n*2;i++)
		  printf("%c\n",result[i]);
    return 0;
}
//

#c언어 자료구조중에서 스택에 대해서 배운것을 활용해보았다!
