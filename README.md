# 📚 Django 로컬 도서관 (Local Library)

이 프로젝트는 Django로 작성된 튜토리얼 웹사이트인 "Local Library"입니다.  
자세한 내용은 [MDN 튜토리얼 홈 페이지](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Tutorial_local_library_website)에서 확인할 수 있습니다.

---

## 📌 개요 (Overview)

이 웹 애플리케이션은 **작은 지역 도서관의 온라인 카탈로그**를 구현합니다. 사용자는 이용 가능한 책을 둘러보고 계정을 관리할 수 있습니다.

현재 구현된 주요 기능은 다음과 같습니다:

- 책, 책 복사본, 장르, 언어, 저자에 대한 **모델**이 구현되어 있습니다.
- 사용자는 **책과 저자 목록 및 상세 정보**를 볼 수 있습니다.
- **관리자(admin)** 사용자는 모델을 생성하고 관리할 수 있습니다.  
  `admin.py`에 등록 코드는 주석 처리되어 있지만, 관리 기능은 최적화되어 있습니다.
- **사서(librarian)**는 예약된 책의 대출 기간을 연장할 수 있습니다.

📌 모델 구조 다이어그램:  
![로컬 도서관 모델](https://raw.githubusercontent.com/mdn/django-locallibrary-tutorial/master/catalog/static/images/local_library_model_uml.png)

---

## 🚀 빠른 시작 (Quick Start)

이 프로젝트를 로컬 환경에서 실행하려면 다음 절차를 따르세요: (본인은 네이버 클라우드 환경에서 실행했습니다)

---

### 1. Python 개발 환경을 설정합니다  
[Python 개발 환경 설정 가이드](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/development_environment)를 참고하세요.  
가상환경(Virtual Environment)을 사용하는 것을 권장합니다.

> ⚠️ **주의:** 이 프로젝트는 Django 3.10 버전에서 테스트되었으며, 다른 버전에서는 정상 작동하지 않을 수 있습니다.

---

### 2. 프로젝트 실행 명령어

아래 명령어들은 Python이 설치되어 있다는 전제 하에 실행합니다.  
Windows에서는 `python` 대신 `py` 또는 `py -3`을 사용할 수 있습니다.

```bash
pip3 install -r requirements.txt
```
> 의존성 패키지들을 설치합니다 (`Django`, `psycopg2-binary`, `gunicorn` 등)
> <br/>본인은 python3.8.10에서 설치를 진행했으므로 Django 라인은 주석처리 후 진행

```bash
python3 manage.py makemigrations
```
> 모델 변경 사항을 감지해 마이그레이션 파일을 생성합니다

```bash
python3 manage.py migrate
```
> DB 스키마를 실제 데이터베이스에 적용합니다

```bash
python3 manage.py collectstatic
```
> 정적 파일을 모아줍니다 (배포용)

```bash
python3 manage.py test
```
> 기본 테스트를 실행합니다 (모든 테스트가 통과해야 합니다)

```bash
python3 manage.py createsuperuser
```
> 관리자 계정을 생성합니다 (ID, 이메일, 비밀번호 입력 필요)

```bash
python3 manage.py runserver 0.0.0.0:8000
```
> 서버를 실행합니다 (기본 포트는 `http://127.0.0.1:8000/`)
> <br/>클라우드 환경에서 접속하는 경우 locallibrary/settings.py에서 ALLOW_HOSTS에 본인 서버 공인 IP 추가 필요
---

### 3. 사이트 접속

- 관리자 페이지:  
  👉 `http://127.0.0.1:8000/admin/`  
  → 여기에 접속해 관리자 계정으로 로그인하고 테스트 데이터를 생성합니다.

- 메인 페이지:  
  👉 `http://127.0.0.1:8000/`  
  → 생성한 책, 저자 등의 정보를 확인할 수 있습니다.

---

필요하시면 해당 프로젝트의 설정(`settings.py`), 데이터베이스 연결, 또는 배포 방법(Docker, Gunicorn, Nginx 등)도 설명해드릴 수 있습니다.
