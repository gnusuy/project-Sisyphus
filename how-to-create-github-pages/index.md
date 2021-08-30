**Github pages를 생성하는 방법**

> _quest들을 기록하기 위해 블로그를 개설하기로 했고, Github에서 제공하는 Github pages 를 활용하기로 했다._ 

<br>

**0. 먼저 [Github](https://github.com) 에 접속해서 회원가입을 한다.** <br>

**1. Github 에서 저장소(Repository)를 만든다.**<br><br>
<img src= "https://github.com/gnusuy/project-Sisyphus.github.io/blob/main/how-to-create-github-pages/1.png?raw=true" width="700" ><br><br>
<img src= "https://github.com/gnusuy/project-Sisyphus.github.io/blob/main/how-to-create-github-pages/2.png?raw=true" width="700" ><br>

   > - Repository name : <사용자명>.github.io 혹은 <프로젝트/조직명>.github.io 로 명명한다.<br>
   > - Description : 저장소에 대한 상세 설명을 쓸 수 있다. (선택) <br>
   > - Public/Private : 저장소를 공개하거나 비공개하여 사용할 수 있다.   
 
<br>

**2. 방금 만든 Github 저장소의 페이지에 들어가서 Settings 를 누른다.**<br><br>
   <img src= "https://github.com/gnusuy/project-Sisyphus.github.io/blob/main/how-to-create-github-pages/2.5.PNG?raw=true" width="700" ><br>
**3. [Settings] 페이지를 쭉 내리면 [GitHub Pages] 항목이 보인다.** <br>
   <img src= "https://github.com/gnusuy/project-Sisyphus.github.io/blob/main/how-to-create-github-pages/3.png?raw=true" width="700" ><br>
**4. [None]으로 선택된 상자를 클릭해서 자신이 보여주고자 하는 브랜치(Branch)를 [main]으로 선택하고, [Save] 버튼을 누른다.**<br>
   <img src= "https://github.com/gnusuy/project-Sisyphus.github.io/blob/main/how-to-create-github-pages/4.png?raw=true" width="700" ><br><br>  
**5. 페이지가 개설되었고, 알려준 주소를 복사해서 접속한다.**<br><br>
   <img src= "https://github.com/gnusuy/project-Sisyphus.github.io/blob/main/how-to-create-github-pages/5.png?raw=true" width="700">
   
 > 링크를 받았어도 바로 접속되지 않는 경우가 있으나, 3~5분 정도 기다렸다가 재접속을 하면 정상적으로 작동한다.

<br>

**6. 개설된 페이지를 확인한다.** <br><br>

<img src= "https://github.com/gnusuy/project-Sisyphus.github.io/blob/main/how-to-create-github-pages/6.PNG?raw=true" width="700" border="20px"> <br>
<img src= "https://github.com/gnusuy/project-Sisyphus.github.io/blob/main/how-to-create-github-pages/7.PNG?raw=true" width="700" border="20px">

> 개설된 페이지 링크로 접속해보면 저장소에 있는 README.md 파일의 내용이 표시된다. 나는 README.md 파일을 index.md 로 이름을 변경해서 사용하고 있다.

<br>

**6-1. 페이지 안에 다른 페이지를 넣고 싶은데 어떻게 해야하나?** <br>

> 처음에는 마크다운 파일에서 활용되는 문법을 써서 열고 싶은 파일의 하이퍼링크를 직접 걸었다. 그랬는데 한글이 다 깨져서 나왔다.<br>
>  ``` 01. [Github pages를 생성하는 방법](https://gnusuy.github.io/project-Sisyphus/how-to-create-github-pages/index.md)``` (<-이 내용을 md 파일에 넣고 하이퍼링크 버튼을 만들었다.) 

<br>

[Github pages를 생성하는 방법](https://gnusuy.github.io/project-Sisyphus/how-to-create-github-pages/index.md)

<br>

<img src= "https://github.com/gnusuy/project-Sisyphus.github.io/blob/main/how-to-create-github-pages/8.PNG?raw=true" width="700"><br>

> 그래서 나는 해당 md파일을 포함하는 폴더를 직접 만들어서 저장소에 업로드했다.<br>
해당 폴더 안의 index.md 파일을 만들어주고 원하는 내용을 해당 파일에 넣었다.<br> 
그리고 링크를 https://<블로그주소>/<폴더명> 으로 입력해서 접속하니 한글도 정상적으로 노출되었다.

>  ``` 01. [Github pages를 생성하는 방법](https://gnusuy.github.io/project-Sisyphus/how-to-create-github-pages)``` (<- 폴더를 만들고 주소를 이렇게 하니 됐다.)

<br> 

[Github pages를 생성하는 방법](https://gnusuy.github.io/project-Sisyphus/how-to-create-github-pages)

