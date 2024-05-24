# Chapter 01. 다트입문하기

## 1.1 다트소개
- 구글이 개발한 멀티 플랫폼 상에서 동작되도록 하는 앱을 위해 디자인된 프로그래밍 언어.(2011)
- 기존 프로그램 언어들과 유사.
- 플랫폼 환경
  + 데스크탑, 모바일 앱 - Dart Native :  JIT(Just-In-Time) 컴파일러, AOT(Ahead-Of-Time) 컴파일러
  + 웹 - Dart Web : 개발 타임 컴파일러(dartdevc), 프로덕션 타임 컴파일러(dart2js)

## 1.2 기초문법
### 메인함수
- 진입점으로 main() 함수 사용.
- print 함수로 값 출력.
- 세미 콜론으로 코드 라인이 끝났음을 알림. 
<pre>
<code>
void main() {
  
print("hello world");
  
}
</code>
</pre>

### 주석
- 한줄 주석 //
- 영역 주석 /* */
- 문서 주석 ///

<pre>
<code>
//이부분은 한줄 주석입니다.  

/* 영역 주석.
print("hello world");
*/

/// 문서주석
/// 멀티라인 주석
</code>
</pre>

### 변수선언
- var : 명시적으로 테이터 타입을 선언하지 않고 사용.
- dynamic : var와 유사하나 다른 타입의 값을 허용함.
- String,int,double,bool 등 : 명시적 데이터 타입 선언.
- final: 한 번 값을 대입하면 변경할 수 없음. 실행될 때 해당 위치에서 값이 결정.
- const: 한 번 값을 대입하면 변경할 수 없음. 컴파일시에 값이 결정.
<pre>
<code>
var name1 ="대한민국";

dynamic name2 = "대한민국";
name2 = 1;

String name3 = "대한민국";
int cnt = 10 + 1;

final log1 = DateTime.now();
//const 부분은 오류발생
const log2 = DateTime.now();

</code>
</pre>

### 컬렉션
#### List
- 여러값이 순서대로 나열된 변수의 집합.
- List형으로 선언 후 리스트명[인덱스] 형태로 값을 조회.
- add : List에 값 추가.
- insert : List에 값 삽입.
- where : List에서 특정 값을 찾음.
- map : List를 순환하면서 값을 변경.
- reduce : List 요소를 하나씩 꺼내서 연산을 하는데 그 결과를 누적하는 함수. 
- fold : reduce와 같지만 시작 인덱스를 지정.

<pre>
<code> 
List<dynamic> testList = ["서울","대전",3,"부산"];
print(testList[testList.length - 2]);

testList.add("인천");
print(testList);

testList.insert(2, "광주");
print(testList);

List<dynamic> testWhere= testList.where((val)=> val=="광주" || val==3).toList();
print(testWhere);

final testMap = testList.map((val) => "제주").toList();
print(testMap);

const testList2 = [1,2,3,4,5];
final testReduce = testList2.reduce((val1,val2) => val1 + val2);
print(testReduce);

final testFold = testList2.fold(1, (val1,val2)=> val1 + val2);
print(testFold);

</code>
</pre>

#### Set
- 중복없는 값들의 집합.
- List형을 Set형으로 변환하면 중복 값들이 제거.
<pre>
<code> 
 List<String> testList = ["서울","대전","대구","대구","부산"];

 print(testList.toSet());
 print(Set.from(testList));
 print(testList.toSet().toList());
</code>
</pre>

#### Map
- 키(key), 값(value)로 짝지어져 있는 iterable.
- 키값을 이용하여 값을 빠르게 찾을 수 있음.
<pre>
<code> 
Map<String,String> testMap =  { "seoul":"서울","pusan":"부산", "incheon": "인천", "incheon": "인천2"  };
  
print(testMap);
print(testMap.keys);
print(testMap.values);
print(testMap["pusan"]);
print(testMap["incheon"]);
</code>
</pre>
#### enum
- 변수의 값이 제한적일때 명확하게 관리하기 위해서 사용.
<pre>
<code> 
enum Korea {
 Seoul,
 Daegu,
 Busan
}

Korea korea = Korea.Busan;
print(korea);

</code>
</pre>

### 연산자
#### 기본연산자
<pre>
<code> 
double num = 2.0;

print(num + 2);
print(num - 2);
print(num * 2);
print(num / 2);
print(num % 2);
print("-------");
print(++num);
print(--num);
print("-------");
print(num += 2);
print(num -= 2);
print(num *= 2);
print(num /= 2);
</code>
</pre>

#### null 연산자
- 다트에서는 변수가 null을 가질수 있는지 타입뒤에 ?로 표시.
- ??= 는 변수값이 null일 경우에만 값을 넣을 수 있음.
<pre>
<code> 
double? nullValue;
print(nullValue);

nullValue ??= 5;
print(nullValue);

nullValue ??= 6;
print(nullValue);
</code>
</pre>

#### 값 비교 연산자
<pre>
<code> 
int number1 = 1;
int number2 = 2;

print(number1 > number2);
print(number1 < number2);
print(number1 >= number2);
print(number1 <= number2);
print(number1 == number2);
print(number1 != number2);
</code>
</pre>

#### 타입 비교 연산자
- == 대신 is를 != 대신 is!으로 자료형 타입을 비교.
<pre>
<code> 
var num = 1.0;
var str = "ABC";

print(num is int);
print(str is String);
print(num is! int);
print(str is! String);
</code>
</pre>

#### 논리 연산자
- and는 && , or는 ||로 표현.
<pre>
<code> 
bool ret = (11 > 10 && 12 > 10);
print(ret);
ret = (11 > 10 || 12 > 10);
print(ret);
</code>
</pre>

### 제어문
#### if 문
<pre>
<code> 
 int val = 10;

 if(val < 9){
  print("$val > 9");
 }
 else if (val >= 10) {
  print("$val >= 10");
 }
 else {
   print("else");
 }
</code>
</pre>
#### switch 문
<pre>
<code> 
 
Korea kr = Korea.Busan;

switch(kr)
{
  case Korea.Daegu:
   print("대구");
   break;

  case Korea.Seoul:
    print("서울");
   break;

  default:
   print("부산");
   break;
}
</code>
</pre>
#### for 문
- 일반적인 for문 이외 컬렉션을 순회하는 for in문 지원.
<pre>
<code> 
for(int i= 1; i <= 10; i++) {
   print(i);
}

List<String> testList = ["서울","대전","대구","부산"];
for(String st in testList){
     print(st);
  }
</code>
</pre>
 
#### while, do while문
<pre>
<code> 
int i = 1;

 while(i <= 10){
  print(i++);
 }

 i = 1;
 do
 {
    print(i++);
 }while(i <= 10);
</code>
</pre>

### 함수
- 함수는 여러번 재사용할 수 있으며 리턴값이 없을때는 void, 있을때는 명시적으로 표기를 해주거나 생략 가능.
- 파라미터로 변수를 전달 할 수 있음.
- 파라미터 전달 방식에는 고정 파라미터,이름 파라미터 형태가 있음.
- 함수는 받는 파라미터에 기본값을 지정할 수 있음.
<pre>
<code>
void main() {
  
print(addTwoNumber(5, 6));
print(addTwoNumberRequired(a:4, b:5));
print(addTwoNumberAndRequire(1, b:2));

print(addTwoNumberDefault(5));
print(addTwoNumberRequiredDefault(a:7));
}

int addTwoNumber(int a, int b)
{
  return a + b;
}

int addTwoNumberRequired({required int a, required int b})
{
 return a + b;
}

int addTwoNumberDefault(int a, [int b = 3])
{
  return a + b;
}

int addTwoNumberRequiredDefault({required int a, int b = 9})
{
 return a + b;
}

int addTwoNumberAndRequire(int a, { required int b })
{
 return a + b;
}
</code>
</pre>

### typedef
- 복잡한 구조의 함수 타입을 미리 정의하여 재사용성을 높일 수 있음.
- 변수처럼 함수에 파라미터로 전달 가능.
<pre>
<code>

typedef operation = int Function(int x, int y);

void main() {

operation oper = addTwoNumber;
print(oper(1,3));
oper = addTwoNumberDefault;
print(oper(2,7));
calculate(5,9,oper);
 
}

void calculate(int x, int y, operation oper)
{
  print(oper(x,y));
}
 
</code>
</pre>

### try..catch 구문
- try 구문에서 오류가 발생 했을시 catch 구문의 코드를 실행.
- throw 로 강제로 오류를 발생시킬 수 있음.
- catch 는 오류구문을 파라미터로 받을 수 있음.
<pre>
<code> 
try{
      throw Exception("오류발생");
      print("a");
    }
catch(e)
  {
    print(e);
  }
</code>
</pre>
