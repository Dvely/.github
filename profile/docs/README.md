# Qeploy GitHub Profile Assets

이 디렉터리는 Dvely 조직 README에서 사용하는 자료를 관리합니다.

## Folder Structure

```text
profile/
├── README.md
├── assets/
│   ├── brand/
│   │   ├── qeploy/                       # 제품 로고 (README 머리글)
│   │   └── dvely/                        # 팀 로고 패키지 — 안내는 dvely/README-KO.md
│   ├── service/
│   │   └── qeploy-service-hero.png
│   └── presentations/
│       ├── midterm/                      # 1학기 중간발표 (프로젝트 제안서) 10장
│       ├── final/                        # 1학기 최종발표 15장
│       └── semester2/                    # 2학기 발표 31장
│           ├── 01-cover.png
│           ├── 02-contents.png
│           └── ...
└── docs/
    ├── README.md
    └── semester2-presentation.pdf        # 2학기 발표 전체 (31쪽)
```

## Image Path Rule

조직 README는 `profile/README.md`에서 렌더링되므로 이미지 경로는 아래처럼 작성합니다.

```md
<img src="./assets/presentations/semester2/10-system-architecture.png" />
<img src="./assets/brand/dvely/Dvely-Logo-Primary.svg" />
```

## 2학기 발표 자료 갱신

원본은 Figma Slides 파일입니다. 슬라이드를 고친 뒤에는 다음 순서로 갱신합니다.

1. 숨기지 않은 슬라이드를 1920 × 1080 PNG로 내보내 `assets/presentations/semester2/`의 같은 파일명으로 덮어씁니다. 파일명은 `NN-영문-요약.png` 형식입니다.
2. 같은 PNG를 순서대로 묶어 `docs/semester2-presentation.pdf`를 다시 만듭니다.
3. 슬라이드 수나 제목이 바뀌었으면 `profile/README.md`의 발표 자료 표도 고칩니다.

## Upload Rule

GitHub에는 ZIP 파일 자체를 올리지 말고, 압축을 푼 뒤 `profile` 폴더를 `.github` 레포 루트에 업로드합니다.

최종 경로는 다음과 같아야 합니다.

```text
Dvely/.github/profile/README.md
```
