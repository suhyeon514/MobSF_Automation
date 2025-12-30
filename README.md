
```markdown
**MobSF Automated Dynamic Analysis Tool**

MobSF(Mobile Security Framework)를 활용하여 안드로이드 앱의 정적/동적 분석을 자동화하고, Custom Frida Script를 주입하여 보안 우회 및 후킹을 수행하는 Python 자동화 도구

## 🛠️ 사전 요구사항 (Prerequisites)

이 도구를 사용하기 위해서는 다음 환경이 구성되어야 합니다.

* Python 3.x
* [MobSF](https://github.com/MobSF/Mobile-Security-Framework-MobSF) (로컬 서버 혹은 원격 서버 구동 중일 것)
* Genymotion 또는 Android Emulator (MobSF와 연결된 상태)

## 📦 설치 및 설정 (Installation & Setup)

1. **레포지토리 클론**
   ```bash
   git clone [레포지토리 주소]
   cd [프로젝트 폴더]

```

2. **의존성 라이브러리 설치**
```bash
pip install requests python-dotenv

```


3. **환경 변수 설정 (중요!)**
이 프로젝트는 `.env` 파일을 사용하여 설정을 관리합니다.
프로젝트 루트 경로에 `.env` 파일을 생성하고 아래 내용을 채워주세요.
**`.env` 작성 예시:**
```ini
# MobSF 서버 주소 (예: [http://127.0.0.1:8000](http://127.0.0.1:8000))
MOBSF_URL=http://localhost:8000

# MobSF API Key (MobSF 상단 메뉴 API Key 복사)
API_KEY=YOUR_MOBSF_API_KEY_HERE

# 분석할 APK 파일의 절대 경로
APK_PATH=D:/Path/To/Your/sample.apk

# 결과 리포트를 저장할 폴더 경로
REPORT_DIR=./reports

# (선택) 타겟 에뮬레이터 ID (adb devices로 확인)
ADB_DEVICE_ID=emulator-5554

```



## 🚀 사용 방법 (Usage)

1. MobSF 서버를 실행합니다.
2. 에뮬레이터를 실행하고 MobSF와 연결되었는지 확인합니다.
3. 스크립트를 실행합니다.

```bash
python dynamic.py

```

스크립트가 실행되면 자동으로 APK를 업로드하고, Frida 스크립트를 주입한 뒤 60초간 동작을 모니터링합니다. 완료 후 `REPORT_DIR`에 `dynamic_result.json` 파일이 생성됩니다.

## 📂 파일 구조 (File Structure)

* `dynamic.py`: MobSF API와 통신하며 전체 분석 과정을 제어하는 메인 스크립트
* `frida_script.js`: 분석 대상 앱에 주입되는 JavaScript 후킹 코드 (보안 우회 로직 포함)
* `.env`: (Git 제외됨) API 키 및 경로 설정 파일

## ⚠️ 주의사항 (Disclaimer)

이 도구는 **교육 및 보안 테스트 목적**으로만 사용해야 합니다. 허가받지 않은 앱에 대해 악의적인 목적으로 사용할 경우 법적 책임을 질 수 있습니다.

```
