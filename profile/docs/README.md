# Qeploy GitHub Profile Assets

이 디렉터리는 Dvely 조직 README에서 사용하는 자료를 관리합니다.

## Folder Structure

```text
profile/
├── README.md
├── assets/
│   ├── service/
│   │   └── qeploy-service-hero.png
│   └── presentations/
│       ├── midterm/
│       │   ├── 01-cover.png
│       │   ├── 02-overview.png
│       │   └── ...
│       └── final/
│           ├── 01-cover.png
│           ├── 02-problem-definition.png
│           └── ...
└── docs/
    ├── README.md
    ├── midterm-presentation.pdf        # 선택 추가
    ├── final-presentation.pdf          # 선택 추가
    ├── midterm-presentation.pptx       # 선택 추가
    └── final-presentation.pptx         # 선택 추가
```

## Image Path Rule

조직 README는 `profile/README.md`에서 렌더링되므로 이미지 경로는 아래처럼 작성합니다.

```md
<img src="./assets/service/qeploy-service-hero.png" />
<img src="./assets/presentations/final/06-system-architecture.png" />
```

## Upload Rule

GitHub에는 ZIP 파일 자체를 올리지 말고, 압축을 푼 뒤 `profile` 폴더를 `.github` 레포 루트에 업로드합니다.

최종 경로는 다음과 같아야 합니다.

```text
Dvely/.github/profile/README.md
```
