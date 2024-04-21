## 도커 wsl 이슈 해결(윈도우)

- 하이퍼-v 설치이후 해결되었다.
  - pushd "%~dp0"
    dir /b %SystemRoot%\servicing\Packages\*Hyper-V*.mum >hyper-v.txt
    for /f %%i in ('findstr /i . hyper-v.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"
    del hyper-v.txt
    Dism /online /enable-feature /featurename:Microsoft-Hyper-V -All /LimitAccess /ALL
    pause
- 위 내용을 C>user>사용자명 안에 넣고 Hyper-V.bat로 확장자를 
  바꾸고 관리자 권한으로 설치하면 된다.
- 이후 재부팅하여 해결하였다.