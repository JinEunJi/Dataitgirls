# Anagram

#### Python

문제 : 두 단어를 입력 받아 이들이 `anagram`인지 판별하라. 
`anagram`이란 단어의 글자를 움직여서 만들 수 있는 다른 단어를 말하는데, 예를 들어 'listen'과 'silent'는 anagram입니다. 각 단어의 글자를 움직이면 상대 글자를 만들 수 있죠. 아나그램을 판별하는 함수를 만들어보시면 될 것 같습니다. **이때 입력은 영어 소문자로 된 단어만 받습니다.** 



##### 처음 생각한 방법 

글자를 정렬하여,  같은지 비교하기

```python
def are_anagram(s1,s2):
    return sorted(s1) == sorted(s2)
```



##### 리스트 이용하기

```python
def are_anagram(s1, s2):
    count = [0]*26
    for c in s1:
        if ord(c) < ord('a') | ord(c) > ord('z') :
            print('소문자만 입력해주세요.')
        count[ord(c) - ord('a')] += 1

    for c in s2:
        if ord(c) < ord('a') | ord(c) > ord('z') :
            print('소문자만 입력해주세요.')
        count[ord(c) - ord('a')] -= 1

    return all(i == 0 for i in count)
```

- ord()는 문자의 ASCII 코드값을 알려주는 함수



##### 딕서녀리 이용하기

```python
def are_anagram(s1, s2):
    count = {}
    for c in s1:
        count[c] = count.get(c, 0) + 1
    for c in s2:
        count[c] = count.get(c, 0) - 1
    return all(i == 0 for i in count.values())
```

- 파이썬은 딕셔너리라는 자료구조가 있는데, Key 와 value로 짝지어져 있으며 {key : value} 로 사용한다. 
- get() 함수는 키 값을 이용해 딕셔너리의 값을 가져온다. get(key, 0) 에서 0은 key와 맞는 데이터가 없을 경우 0으로 가져 오겠다는 뜻. 

