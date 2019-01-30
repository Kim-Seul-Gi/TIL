# 190130 algorithm

## 0. remind

```python
mylist = list(map(int, input().split()))
# 이런 방법 말고

a, b, c, d = map(int, input().split())
# 이렇게 적용하여도 각 변수에 숫자가 적용될 수 있다.
```



## 1. 문자열

문자 a 에 대한 이진수가 존재함. > ASCII

bit 0/1

8bit - 1byte, 하나의 아스키 코드(7bit)+패리티 비트(1bit) 를 담을 수 있음

다국어 처리를 위해 유니코드 가 마련됨. > 2^16 에 전세계 문자를 다 넣음.

### 1-1. 문자열 <> 배열

- 문자열>배열>문자열 자유롭게 바꾸기 word='1234'이더라도 1, 2 이런것 각 각은 문자열로 인식
  - 그리고 문자열은 바로 배열로 변환이 가능(word_list2)하기도 하다.

```python
word='Reverse this strings'
print(word) 
>> Reverse this strings

word_list=list(map(str,word))
print(word_list) 
>> ['R', 'e', 'v', 'e', 'r', 's', 'e', ' ', 't', 'h', 'i', 's', ' ', 's', 't', 'r', 'i', 'n', 'g', 's']

word_list2=list(word)
print(word_list2)
>> ['R', 'e', 'v', 'e', 'r', 's', 'e', ' ', 't', 'h', 'i', 's', ' ', 's', 't', 'r', 'i', 'n', 'g', 's']


word_after=''.join(word_list)
print(word_after)
>> Reverse this strings
```



- 배열>문자열>배열 : 배열 안 원소가 문자형이면, join으로 바로 가능하지만, 

  배열 안 원소가 int 형식이라면 str 형식으로 mapping 과정을 거친 후 join 해야한다!

  - 배열을 str 처리를 하면 []과 , 이나 공백을 포함한 모든 것들이 문자로 처리되어서 저장된다.

``` python
a=[1,2,3]
b=str(a)
print(b[3]) >> 공백

for i in range(5):
    print(b[i])
​```
[
1
,
공백
2
​```
    
```

```python
a=['1','2','3','4']
print(''.join(a))
>> 1234
```

```python
a=[1,2,3,4]
b=list(map(str,a))
print(''.join(b))
>>  1234

a=[1,2,3,4]
b=list(map(str,a))
c=''.join(b)
print(c) # 이것과 같은 의미이다. join함수는 반환 값이 있다는 것을 의미한다.
```



### 1-2. strcmp(a, b)

<strong>a랑 b가 서로 같은 문자열인지를 확인하는 함수.</strong>

- python에서는 a==b와 같은 의미. 직접 함수를 구현할 수도 있다.
  - (1) 두 문자의 길이가 같은지?
  - (2) 두 문자의 모든 요소가 같은 값인지?

```python
def strcmp(a,b):
    if len(a) != len(b):
        return False
    else:
        for i in range(len(a)):
            if a[i]!=b[i]:
                return False
        return True

def strcmp2(a,b):
    if len(a) != len(b):
        return False
    else:
        i = 0
        while i < len(a):
            if a[i]!=b[i]:
                return False
            else:
                i+=1

    return True

a='abc'
b='abcb'
print(strcmp(a,b)) >> False
print(strcmp2(a,b)) >> False
print(a==b) >> False
```



### 1-3. atoi(string)

주어진 문자를 int 형으로 반환하는 함수 ex, '123' > 123

```python
# ord(x) : 문자 x의 유니코드 코드값을 ex, ord(0) >> 48
# chr(x) : 코드값 x에 대한 문자를 출력 ex, chr(48) >> 0

def atoi(string):
    value = 0
    i = 0
    while (i < len(string)):
        c = string[i]
        print(type(c)) >> str
        if c >= '0' and c <= '9' : 
            # c는 문자이지만, '0','9' 같이 있어도 비교가능
            digit = ord(c) - ord('0')
        else:
            break
        value = (value * 10) + digit
        i +=1
    return value

a='123'
print(type(a)) >> str

b=atoi(a)
print(b) >> 123
```



### 1-4 itoa(x)

주어진 int 형 숫자를 문자로 바꾸는 방법 : ex, 123(int) > 123(str)

```python
def itoa(x):
    list1=[]

    while x > 0:

        list1.append(x % 10)

        x = x//10
    b=list1[::-1]
    c=''.join(list(map(str,b)))
    return c

print(itoa(123)) 
```





