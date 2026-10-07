# ledger-api — 가계부 API (FastAPI + Supabase PostgreSQL)

- GitHub: https://github.com/chloeyschung/ledger-api
- Render: (배포 후 기입)

클라우드컴퓨팅실습 4주차 과제. FastAPI + SQLAlchemy 2.0으로 만든 가계부 API를 Render에 배포하고, 환경변수 `DATABASE_URL`로 Supabase(PostgreSQL, Session pooler)에 연결한다.

## 엔드포인트

| 메서드 | 경로 | 설명 |
|---|---|---|
| POST | `/accounts` | 계좌 생성 |
| GET | `/accounts` | 계좌 목록 |
| GET | `/accounts/{account_id}` | 계좌 단건 조회 |
| POST | `/transactions` | 거래 생성 (계좌 외래키) |
| GET | `/accounts/{account_id}/detail` | 계좌 + 거래 목록 중첩 응답 |
| GET | `/stats/by-category` | 카테고리별 지출 합계 (GROUP BY) |

## 실행

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
# .env 에 DATABASE_URL=postgresql+psycopg://postgres.<ref>:<비밀번호>@<host>.pooler.supabase.com:5432/postgres
uvicorn main:app --reload
```

## Render 설정

- Build Command: `pip install -r requirements.txt`
- Start Command: `uvicorn main:app --host 0.0.0.0 --port $PORT`
- Environment Variable: `DATABASE_URL` (Supabase Session pooler 연결 문자열)
