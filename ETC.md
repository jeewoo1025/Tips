## Visual Studio Tools 설치
* link : https://visualstudio.microsoft.com/ko/thank-you-downloading-visual-studio/?sku=BuildTools

설치 완료 후, cmd 창에서 다음의 명령어를 실행하면 
Microsoft (R) C/C Optimizing Compiler 라는 이름을 볼 수 있다. 
바로 이것이 일반적으로 Visual Studio 에서 C 혹은 C++를 사용할 때 사용하는 컴파일러의 이름이다.
```python
> "C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\BuildTools\\Common7\\Tools\\VsDevCmd.bat"
> cl
```
<br>

## vscode Python에서 argument가 있는 파일 디버그방법
launch.json 파일에서 `"args":[]` 생성 → 구성 추가 → 순서대로 문자열 타입으로 arguments 입력 → 실행
* link : https://zosystem.tistory.com/282
