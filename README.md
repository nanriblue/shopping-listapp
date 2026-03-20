# 쇼핑 리스트 앱

간단한 쇼핑 리스트 웹 애플리케이션입니다. HTML, CSS, JavaScript로 구성되어 있으며, Supabase 데이터베이스를 사용하여 데이터를 저장합니다.

## 기능

- 쇼핑 아이템 추가 / 삭제
- 체크(완료) 표시
- Supabase 데이터베이스 기반 데이터 저장 (클라우드 동기화)
- 남은 아이템 수 표시

## 사전 준비 (Supabase 설정)

Supabase 대시보드의 SQL Editor에서 아래 SQL을 실행하여 테이블을 생성합니다:

```sql
CREATE TABLE shopping_items (
  id BIGINT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
  name TEXT NOT NULL,
  checked BOOLEAN DEFAULT FALSE,
  created_at TIMESTAMPTZ DEFAULT NOW()
);

ALTER TABLE shopping_items ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Allow all access" ON shopping_items
  FOR ALL USING (true) WITH CHECK (true);
```

## 실행 방법

1. 저장소를 클론합니다:
   ```bash
   git clone git@github.com:nanriblue/shopping-listapp.git
   ```
2. 위 Supabase 테이블 설정을 완료합니다.
3. `public/index.html` 파일을 브라우저에서 열면 바로 사용할 수 있습니다.

## 프로젝트 구조

```
shopping-listapp/
├── public/
│   └── index.html    # 메인 앱 (HTML/CSS/JS)
├── .gitignore
├── CLAUDE.md
└── README.md
```
