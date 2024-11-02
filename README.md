# how to use branch
***
## 브랜치 목록 확인
### 로컬 브랜치 목록 확인
현재 체크아웃 중인 브랜치 *로 표시

```git branch
```

### 원격 브랜치 목록 확인
```
git branch -r
```

## 로컬
### 로컬에서 브랜치 생성
```
git branch 브랜치이름
```

### 로컬에서 브랜치 삭제
해당 브랜치가 병합되지 않은 경우 삭제 거부

강제로 삭제하려면 -D 사용

```git branch -d 브랜치이름
```

### 로컬에서 지정한 브랜치로 전환
전환시 현재 작업중인 변경사항이 커밋 되지 않았다면 경고

```git checkout 브랜치이름
```

### 로컬에서 브랜치 생성후 생성한 브랜치로 전환
```git checkout -b 브랜치이름
```

### 로컬에서 원격의 특정 브랜치를 가져와 체크아웃
```git checkout -b 로컬브랜치이름 origin/원격브랜치이름
```

## 원격
### 원격 저장소에 브랜치 푸시
```git push -u origin 브랜치이름
```

### 원격 저장소의 모든 변경 사항 가져오기
로컬과 병합하지 않아 자동반영되지 않음

```git fetch
```

### 특정 원격 저장소의 변경 사항 가져오기
```git fetch 특정 원격 저장소 이름
```

### 특정 원격 브랜치의 변경 사항 가져오기
origin에서 feature-branch 브랜치의 변경 사항만 가져옴

```git fetch origin feature-branch
```

### 원격 저장소에서 삭제된 브랜치를 로컬에서도 제거
원격 저장소에서 모든 변경 사항을 가져오고,

원격 저장소에서 삭제된 브랜치에 대한 로컬 추적 브랜치를 제거

```git fetch --prune
```

### 특정 원격 저장소에서 삭제된 브랜치를 로컬에서도 제거
origin은 특정 원격 저장소의 이름

```git fetch origin --prune
```

## merge
1. merge는 두 개의 브랜치를 통합하여 하나의 브랜치로 결합하는 과정

    주로 로컬에서 사용

    원격에서의 병합은 Pull Request (PR)

1. fast-forward

    A 브랜치에서 다른 B브랜치를 Merge할 때

    B 브랜치가 A 브랜치 이후의 커밋을 가리키고 있으면,

    A 브랜치가 B 브랜치와 동일한 커밋을 가리키도록 이동 시킴

   (A의 커밋이 B의 커밋의 조상일 때, 두 커밋이 커밋 트리의 같은 라인에 있을 때)

1. 3-way-merge

    현재 브랜치가 가리키는 커밋이 merge할 브랜치가 가리키는 커밋의 조상이 아니라면

    각 브랜치가 가리키는 커밋 두개와 공통 조상 하나를 사용하여 3-way-merge 한다.

    3-way-merge의 결과를 별도의 커밋으로 만들고 해당 브랜치가 그 커밋을 가리키도록 이동,

    이런 커밋은 부모가 여러 개고 merge 커밋 이라고 부름

1. 3-way-merge의 충돌

    merge하는 두 브랜치에서 같은 파일의 한 부분을 동시에 수정하고 merge하면

    충돌(conflict) 발생

### 기본 merge
현재 체크아웃된 브랜치에 다른 브랜치를 병합

```git merge 통합하려는 브랜치 이름
```

### 상태 점검
햔재 브랜치와 변경 사항의 상태 확인

병합 후 상태 점검

merge 충돌 발생 시 어떤 파일을 merge할 수 없었는지 점검

```git status
```