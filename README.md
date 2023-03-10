# VSCODE_DEBUG_SETTING


## 디레토리 구조
VSCODE_DEBUG_SETTING

├── _code_sample1.py

├── _folder1

│   └── _module_sample1.py

├── _folder2

│   └── _module_sample2.py

└── README.md

## launch.json 파일 작성 방법

"configurations" : 딕셔너리,{} 를 담은 리스트. 딕셔너리,{} 안에는 디버거 설정값들이 key:value 형식으로 저장됨. {} 하나당 디버거 하나

## "configurations" 안의 특성값들

"name": 문자열. 디버거 이름.

"type": 문자열. 프로그래밍 언어 이름.

"request": 문자열. "launch" 또는 "attach" 디버깅 모드를 launch 방식으로 할지, attach 방식으로 할지 입력. 

The best way to explain the difference between launch and attach is to think of a launch configuration as a recipe for how to start your app in debug mode before VS Code attaches to it, while an attach configuration is a recipe for how to connect VS Code's debugger to an app or process that's already running.(https://code.visualstudio.com/docs/editor/debugging#_launch-versus-attach-configurations)

"program": 문자열. 디버거가 디버깅할때, 처음으로 실행시킬 코드파일의 경로. ${...} 등을 활용하면, 상대경로로 쉽게 작성할 수 있다.

cf)
${workspaceFolder} :  vscode 를 켜면, 처음에 프로젝트를 여는데, 그 프로젝트 폴더의 경로를 의미함.

cf)
${file} : vscode 에서 현재 보고있는(탭 중에서도 선택되어 있는) 코드 파일의 경로를 의미함.


"console": 문자열. Where to launch the debug target: internal console, integrated terminal, or external terminal.

"justMyCode": boolean 값. true 또는 false. user-written code 만을 디버깅할 것인지 아닌지 여부.

"args": 문자열을 담은 리스트. 코드파일 실행시 넘겨줄 argument들을 어절단위로 나눠서, 문자열 리스트로 넣어줌.

"env": 딕셔너리,{}. {}안에서 여러 환경변수를 지정함. key(환경변수):value(값) 형식으로 저장됨. key 와 value 모두 문자열.

cf) "PYTHONPATH" : 디버깅할때 참조할 파이썬 환경변수. 디버깅할때, 이 환경변수에 담긴 경로들을 참조함. :로 여러 패키지 경로들을 구분함. 현재 실행중인 파이썬 코드(.py)에서 메서드를 사용할때, 그 메서드가 현재 실행중인 파이썬 코드안에서 정의되지 않았으면, 컴퓨터는 (1) .py파일이 속한 디렉토리의 절대경로 (2) PYTHONPATH 환경변수 (3) 기타기본경로(파이썬 내장 모듈등의 경로) 순으로 탐색을 한다. 그래서 그 중에서 해당 메서드가 정의된 파일을 찾으면, 탐색을 멈추고, 그 코드를 이용하여 메서드를 동작시킨다.
(참고 : https://www.bangseongbeom.com/sys-path-pythonpath.html)

cf) "CUDA_VISIBLE_DEVICE" : 코드를 돌릴때, 사용할 GPU 번호. ex) "0,1" - 0번과 1번 GPU를 사용하여 코드를 돌림.


## 참고 링크
https://code.visualstudio.com/docs/editor/debugging

틈틈이 읽어보고, 키워드 검색해서도 찾아서 읽어보자. 문서 내용이 좋다. 물론 모든 내용이 다 있는 것은 아니지만.