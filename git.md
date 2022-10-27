# 최초 깃 시작 시 등록정보
```
git config --global core.autocrlf inupt
git config --global user.name 'chancharn'
git config --global user.email 'mchank9191@gmail.com'
```

# 등록한 정보 확인
```
git config --global --list
```

# 현재 프로젝트에서 깃(버전관리/변경사항 추적)을 시작
```
git init
```

# 깃 상태 확인
```
git status
```

# 깃을 stage area에 추가 (commit전 단계)
```
git add .
```

# 버전을 생성해서 깃 커밋
```
git commit -m 'ver.1'
```

# 프로젝트 내용 수정 및 추가 (ex/main.js)
```
git add main.js
git commit -m 'ver.2'
```

# 깃 로그 상태
```
git log
```

---
> 여기까지는 컴퓨터 내에만 등록되어 있는 상태   
> 깃허브에서 레퍼지토리 생성 후
---

# 깃허브에 생성한 원격 저장소와 연결
```
git remote add origin 000(git repository 주소)
```

원격 저장소에 업로드 (master 권한으로)
```
git push origin master
```

> master이라는 기존 큰 줄기를 만든 다음   
세부적인 작업(로그인기능, 검색기능...)을 할 때 branch를 사용한다

# 브렌치 생성
```
git branch signin
```

# master에서 signin으로 브렌치 변경
```
git checkout signin
```

# 위의 두 코드를 한번에 작업(생성&브렌치 변경)
```
git checkout -b 000
```

# branch 상태 확인
```
git branch
```

# 작업 후
```
git status -> git add . -> git commit -m '변경내용'
```

# 원격 저장소로 push
```
git push origin signin (master X)
```

> 깃헙에서 pull request를 통해 merge하면 된다

### 만약 이전 작업 버전으로 돌아가려는 경우 바로 전 단계 버전으로 돌아가는 경우 (2를 넣으면 두단계 전 버전)
```
git reset --hard HEAD~1
```
# reset 사용하기 전 기존 버전으로 이동
```
git reset --hard ORIG_HEAD
```

# 새로운 환경(다른 컴퓨터)에서 작업할 경우
1. git clone 000  
    master 브렌치만 clone가 되는데,   
    원격 저장소의 다른 브렌치들의 존재를 확인하려면,
1. git branch -r  
    로컬에 다른 브렌치도 가지고 오려면
1. git checkout -t origin/가져오려는브렌치명  
    필요없는 브렌치 삭제하려면,
1. git branch -d 000 (삭제하려는 브렌치명)

# 두대의 컴퓨터에서 master로 push를 하다가 충돌나는 경우
com1이 ver3을 수정해서 ver4로 push를 했고,  
com2가 수정된 ver4가 아닌 ver3에다가 수정을 해서 push를 하는 경우   
기존 버전의 충돌이 일어나 push가 이루어지지 않는다.   
이런 경우 com2에서  
git reset --hard HEAD~1로 다시 ver3으로 돌아가서 다시 진행하면 되지만,  
다시 돌아가기엔 com2에서 작업한 양이 많아 돌아가기 어려운 상황이면,   
`git pull origin master`  
입력해서, com1에서 push한 내용을 갖고 와 com2에서 작업한  
충돌난 부분을 하나하나 확인 가능