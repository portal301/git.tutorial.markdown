# Chapter 4

## 학습 목표
- Pull Request 사용해보기
- 이상적인 PR과 커밋의 코드 변경량

## Pull Request 사용해보기

Pull Request(PR)는 협업 환경에서 코드 변경 사항을 검토하고 병합하기 위한 핵심 도구입니다. PR을 통해 팀원들은 변경된 코드를 검토하고, 피드백을 제공하며, 최종적으로 메인 브랜치에 안전하게 통합할 수 있습니다.

### Pull Request란?

**Pull Request**는 개발자가 자신의 브랜치에서 작업한 내용을 원격 저장소의 메인 브랜치에 병합해 달라고 요청하는 과정입니다. PR은 코드 리뷰, 자동화된 테스트 실행, 논의 등을 포함하여 협업의 품질을 높이는 역할을 합니다.

### Pull Request 생성하기

1. **브랜치에서 작업하기**:
   - 새로운 기능이나 버그 수정을 위해 별도의 브랜치를 생성하고 작업을 완료합니다.
    ```bash
    git checkout -b feature/new-feature
    # 코드 수정 및 커밋
    git add .
    git commit -m "FEATURE: 새로운 기능 추가"
    ```
2. **브랜치를 원격 저장소에 푸시하기**:
    ```bash
    git push origin feature/new-feature
    ```
3. **GitHub에서 Pull Request 생성**:
   - GitHub 리포지토리 페이지로 이동합니다.
   - Compare & pull request 버튼을 클릭합니다.
   - PR 제목과 설명을 작성하고, 필요한 경우 리뷰어를 지정합니다.
   - Create pull request 버튼을 클릭하여 PR을 생성합니다.


### Pull Request 리뷰 및 병합
1. **코드 리뷰**:

   - 팀원들은 PR을 검토하며 코드의 품질, 스타일, 기능 등을 확인합니다.
   - 피드백을 제공하고 필요한 수정을 요청할 수 있습니다.

2. **수정 사항 반영**:
   - 요청된 변경 사항을 브랜치에 반영합니다.
        ```bash
        git add .
        git commit -m "FIX: 코드 리뷰 피드백 반영"
        git push origin feature/new-feature
        ```
3. **PR 병합**:
    - 모든 리뷰어의 승인을 받은 후, PR을 메인 브랜치에 병합합니다.
    - GitHub에서는 ```Merge pull request```, ```Squash and merge```, ```Rebase and merge``` 옵션을 제공합니다.

4. **브랜치 삭제**:
    - 병합이 완료된 후, 더 이상 필요하지 않은 브랜치를 삭제하여 리포지토리를 정리합니다.
        ```bash
        git branch -d feature/new-feature
        git push origin --delete feature/new-feature
        ```

### 이상적인 PR과 커밋의 코드 변경량
효과적인 Pull Request와 커밋은 프로젝트의 가독성과 유지보수성을 높입니다. 다음은 이상적인 PR과 커밋의 특징입니다.

### Pull Request의 이상적인 크기
-  작고 명확한 변경 사항: PR은 하나의 명확한 목적을 가져야 합니다. 예를 들어, 하나의 기능 추가나 버그 수정에 집중합니다.
- 짧은 코드 변경량: 너무 많은 파일이나 라인이 변경되지 않도록 합니다. 이는 리뷰어가 효율적으로 코드를 검토할 수 있게 합니다.
- 명확한 설명: PR의 제목과 설명은 변경 사항의 목적과 내용을 명확히 전달해야 합니다.
- 코드의 양은 ```+500``` / ```-500```이 적당합니다. 너무 많은 코드의 양은 리뷰어가 집중하기 어렵게 만듭니다.

### 이상적인 커밋 메시지
- 의미 있는 메시지: 커밋 메시지는 변경 사항의 목적과 내용을 명확히 설명해야 합니다.
- 일관된 포맷: 팀에서 정한 커밋 메시지 규칙을 따릅니다. 예를 들어, ```TYPE: 설명``` 형식을 사용할 수 있습니다.
- ```TYPE```: ```FEATURE```, ```FIX```, ```DOC```, ```STYLE```, ```REFACTOR```, ```TEST``` 등
- 설명: 변경 사항에 대한 간단한 설명
- 짧고 간결하게: 커밋 메시지는 간결하면서도 충분한 정보를 제공해야 합니다.
#### 예시
- ❌ 나쁜 예시
    ```bash
    git commit -m "수정"
    ```
- ⭕ 좋은 예시
    ```bash
    git commit -m "FIX: 로그인 오류 수정"
    git commit -m "FEATURE: 사용자 프로필 페이지 추가"
    ```

## 지금까지 배운 내용 실습해보기
2명 이상 한 조가 되어, 우리는 가상의 프로그램을 제작해볼 예정입니다.

1. 각 조에서 한 명씩 새로운 리포지토리를 생성해보겠습니다.
2. 리포지토리를 클론하고 다른 한 사람이 dev라는 브랜치를 생성해 origin에 푸시합니다.
   <details>
   <summary>예시</summary>
   
   ```bash
   git checkout -b dev
   #혹은
   git branch dev
   git checkout dev
   
   #이후
   git push origin dev
   ````
   </details>

3. 이제 각자 dev 브랜치에서부터 ```Feature/A```, ```Feature/B``` 라는 이름의 브랜치를 생성 후, 파일을 생성하거나 수정해서 커밋을 3개씩 생성합니다.
   <details>
   <summary>예시</summary>
   
   ```bash
   git checkout dev
   git branch Feature/A
   git checkout Feature/A
   
   #파일 생성
   git add .
   git commit -m "FEAT(Filename): 새 파일 생성"

   #생성한 파일 수정
   git add .
   git commit -m "FIX(filename): 생성한 파일의 버그 수정"

   #새 파일 생성
   git add .
   git commit -m "FEAT(newfilename): 새 파일 생성"


   git push origin Feature/A
   ````
   </details>

4. 웹 브라우저로 ```github``` 프로젝트 페이지에 접속해서, ```Feature/A```,와 ```Feature/B``` 각각의 Pull Request를 작성합니다. 이때 베이스 브랜치는 ```dev```입니다.
5. 우선 ```Feature/A```의 Pull Request부터 처리하겠습니다. 이때 ```Feature/B``` 작성자는 Comment를 작성 후, ```Approve```를 눌러봅니다.
6. 첫 번째 **Pull Request(PR)** 가 ```Approve```되었으니, 이제 ```Feature/A```의 **PR**을 ```Merge``` 해봅니다. 이때 방식은 Merge pull Request로 합니다.
7. ```Feature/A```의 작성자는 PR이 Merge된것을 확인 한 후, ```Pull``` 받은 dev 브랜치에서 새로운 ```Feature/C```를 생성한 후, 한개의 커밋을 추가합니다.
   <details>
   <summary>예시</summary>
   
   ```bash
   git checkout dev
   git pull origin dev

   git branch Feature/C
   git checkout Feature/C
   
   #파일 생성
   git add .
   git commit -m "FEAT(Filename): 새 파일 생성"

   # 아직 원격 저장소에 푸쉬하지 않습니다.
   ````
   </details>

8. ```Feature/B```의 작성자는 해당 브랜치의 시작점을 ```Feature/A```가 Merge된 dev로 변경해야합니다. 이번엔 리베이스를 통해 ```Feature/B```의 시작을 변경해봅시다.
   <details>
   <summary>예시</summary>
   
   ```bash
   git checkout dev
   git pull origin dev

   git checkout Feature/B
   git rebase origin/dev
   
   git push origin Feature/B --force 
   ````
   
   **주의**: 리베이스 후에는 --force 옵션을 사용하여 푸시해야 합니다. 이는 원격 브랜치의 히스토리를 변경하므로 팀원들과의 협업 시 주의가 필요합니다.

   </details>
   
9. ```git lg``` 명령어로 ```Feature/B```가 정상적으로 최신의 ```dev``` 브랜치 위에 잇으면 ```Feature/A```의 작성자가 **PR**을 **Approve**하고, Merge pull request 버튼을 누릅니다. 이때 방식은 ```Squash and merge```로 합니다.

10. 마지막으로 같은 방식으로 ```Feature/C```도 dev를 pull 받은 후, 최신화하여 ```Feature/C```를 ```rebase```합니다. 이후 9번과 같은 방식으로 PR을 Merge하되, 방식은 ```Rebase and Merge```로 합니다.
    <details>
    <summary>예시</summary>
    
    ```bash
    git checkout dev
    git pull origin dev

    git checkout Feature/C
    git rebase origin/dev

    # Feature/C는 아직 Origin에 있지 않으므로, --force 명령어가 필요 없습니다.
    git push origin Feature/C 
    ````
    </details>

11. 이제 dev를 pull 받은 후, ```git lg```를 실행해보고, 각 Merge 방식의 차이점에 대해 알아봅시다.

12. dev 브랜치를 main으로 합치는 PR을 작성하고, Merge해봅니다.

13. dev 브랜치를 다시 main의 맨 위로 가도록 rebase합니다.
    <details>
    <summary>예시</summary>
    
    ```bash
    git checkout dev
    git pull origin dev
    git rebase main

    git lg
    ````
    </details>

## Merge 방식의 차이점 이해하기
실습을 통해 사용한 Merge 방식인 Merge pull request, Squash and merge, Rebase and Merge의 차이점을 git lg를 통해 확인해봅시다.

### 1. Merge pull request
- 특징:
    - 브랜치의 전체 히스토리를 유지합니다.
    - 별도의 Merge 커밋이 생성됩니다.
    - 브랜치의 커밋이 모두 보존됩니다.
- 장점:
    - 모든 커밋이 히스토리에 남아 있어 변경 내역 추적이 용이합니다.
    - 병합 시점이 명확히 표시됩니다.
- 단점:
    - 히스토리가 복잡해질 수 있습니다.
    - 불필요한 Merge 커밋이 많이 생길 수 있습니다.
  
### 2. Squash and merge
- 특징:
    - 여러 커밋을 하나의 커밋으로 합칩니다.
    - 브랜치의 히스토리가 간결해집니다.
- 장점: 
    - 히스토리가 깔끔해져 가독성이 높아집니다.
    - 불필요한 커밋이 줄어듭니다.
- 단점:
    - 개별 커밋의 상세 내역이 사라집니다.
    - 특정 변경 사항을 추적하기 어려울 수 있습니다.
### 3. Rebase and Merge
- 특징:
    - 브랜치의 커밋을 현재 dev 브랜치의 최상단으로 이동시킵니다.
    - 병합 커밋 없이 히스토리를 선형으로 유지합니다.
- 장점:
    - 히스토리가 깔끔하고 선형적입니다.
    - Merge 커밋이 없어 히스토리가 단순해집니다.
- 단점:
    - 히스토리가 재작성되므로, 협업 시 주의가 필요합니다.
    - --force 푸시가 필요할 수 있어 실수할 위험이 있습니다.
## 결론

이번 실습을 통해 다양한 Merge 방식인 `Merge pull request`, `Squash and merge`, `Rebase and Merge`의 차이점을 직접 경험하고 이해할 수 있었습니다. 각 Merge 방식은 프로젝트의 히스토리 관리와 협업 효율성에 있어 고유한 장단점을 지니고 있으며, 상황에 따라 적절하게 선택하는 것이 중요합니다.

### 주요 학습 내용 요약

- **Merge pull request**:
  - **장점**: 모든 커밋이 히스토리에 남아 있어 변경 내역을 상세히 추적할 수 있습니다.
  - **단점**: 병합 커밋이 추가되어 히스토리가 복잡해질 수 있습니다.

- **Squash and merge**:
  - **장점**: 여러 커밋을 하나로 합쳐 히스토리가 깔끔해집니다.
  - **단점**: 개별 커밋의 상세 내역이 사라져 특정 변경 사항을 추적하기 어려울 수 있습니다.

- **Rebase and Merge**:
  - **장점**: 히스토리가 선형적으로 유지되어 가독성이 높아집니다.
  - **단점**: 히스토리 재작성으로 인해 협업 시 주의가 필요하며, `--force` 푸시가 요구될 수 있습니다.

### 최적의 Merge 방식 선택하기

프로젝트의 특성과 팀의 협업 방식에 따라 적절한 Merge 방식을 선택하는 것이 중요합니다.

- **프로젝트의 히스토리 가독성**을 중시한다면 `Rebase and Merge`를 고려할 수 있습니다. 선형적인 히스토리는 버그 추적과 코드 이해를 용이하게 합니다.
  
- **모든 커밋 내역을 보존**하고 싶다면 `Merge pull request`가 적합합니다. 이는 특히 중요한 변경 사항이나 복잡한 기능 개발 시 유용합니다.
  
- **히스토리를 간결하게 유지**하고 싶다면 `Squash and merge`를 사용하는 것이 좋습니다. 작은 기능 추가나 간단한 버그 수정에 적합합니다.

### 협업 시 주의사항

- **팀원 간의 합의**: 어떤 Merge 방식을 사용할지 팀원들과 사전에 합의하고, 일관되게 적용하는 것이 중요합니다.
  
- **히스토리 관리**: `Rebase`를 사용할 때는 히스토리가 변경되므로, 팀원들과 충분히 소통하고, 필요 시 강제 푸시(`--force`)의 사용을 신중히 결정해야 합니다.
  
- **코드 리뷰의 중요성**: 모든 Merge 방식에서 코드 리뷰는 필수적입니다. PR을 통해 코드의 품질을 유지하고, 팀원 간의 이해를 높일 수 있습니다.

### 향후 발전 방향

이번 실습을 통해 기본적인 Merge 방식의 차이점을 이해했으므로, 향후에는 다음과 같은 고급 협업 기법을 학습해보는 것이 좋습니다.

- **Git Hooks**: 커밋 전에 자동으로 실행되는 스크립트를 설정하여 코드 품질을 유지합니다.
- **Continuous Integration/Continuous Deployment (CI/CD)**: 자동화된 테스트와 배포 파이프라인을 구축하여 개발 효율성을 극대화합니다.
- **Advanced Rebase Techniques**: 인터랙티브 리베이스(`git rebase -i`)를 활용하여 커밋 히스토리를 더욱 정교하게 관리합니다.

### 마무리

Git의 다양한 Merge 방식을 이해하고 적절히 활용하는 것은 팀 프로젝트에서의 효율적인 협업과 코드 관리에 있어 필수적입니다. 이번 실습을 통해 각 Merge 방식의 특성과 그에 따른 장단점을 체험함으로써, 실제 프로젝트에서 상황에 맞는 최적의 Merge 전략을 선택할 수 있는 능력을 배양했습니다. 앞으로도 지속적인 학습과 실습을 통해 Git 활용 능력을 더욱 향상시켜 나가길 바랍니다. 🚀





