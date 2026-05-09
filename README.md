# AR/MR을 활용한 동물실험 관심 제고 콘텐츠 개발

> HoloLens 2 기반 혼합현실(MR) 교육용 콘텐츠 프로젝트  
> **2022-2학기 개별연구** | CS AR/MR 프로그래밍 기법 연구 및 시각화 프로그래밍 결과물

---

## 📋 목차

- [프로젝트 개요](#-프로젝트-개요)
- [개발 동기](#-개발-동기)
- [기술 스택](#-기술-스택)
- [주요 기능](#-주요-기능)
- [시스템 구조](#-시스템-구조)
- [설치 및 사용 방법](#-설치-및-사용-방법)
- [기대 효과](#-기대-효과)
- [향후 계획](#-향후-계획)

---

## 🎯 프로젝트 개요

본 프로젝트는 **Unity와 MRTK(Mixed Reality Toolkit)** 를 활용하여, 동물 실험에 대한 사회적 논쟁을 사용자가 직접 체험하며 정보를 습득할 수 있는 **HoloLens 2 기반 실감형 콘텐츠**를 개발하는 것을 목적으로 합니다.

### 핵심 목표

- 인간을 위한 동물 실험의 윤리적 대립에 대한 **대중의 관심 제고**
- AR/MR 프로그래밍 기법 파악 및 교육용 교보재 콘텐츠 제작
- **텍스트 중심의 교육**에서 벗어나 **몰입형 트레이닝 시스템** 구축

### 타겟 사용자

동물 실험의 필요성 및 윤리적 문제에 대한 교육이 필요한 사용자

---

## 💡 개발 동기

인간을 위한 동물 실험의 윤리적 필요성과 도덕적 문제에 대한 지속적인 사회적 논쟁이 존재합니다. 본 프로젝트는 최신 기술인 **AR/MR을 통해** 이 주제에 대한 대중의 관심을 높이고, 단순한 정보 전달을 넘어 **직접 체험**하며 이해할 수 있는 환경을 제공하고자 합니다.

---

## 🛠️ 기술 스택

### 개발 환경
| 항목 | 기술 |
|------|------|
| **3D 개발 엔진** | Unity |
| **XR 프레임워크** | AR Foundation |
| **MR 툴킷** | MRTK (Mixed Reality Toolkit) |
| **타겟 디바이스** | Microsoft HoloLens 2 |
| **텍스트 렌더링** | TextMesh Pro |
| **프로그래밍 언어** | C# |

### 핵심 기술 및 라이브러리

- **AR Foundation**: 플랫폼 간 핵심 AR 기능 통합 워크플로우
- **MRTK (Mixed Reality Toolkit)**
  - 공간 상호 작용 및 UI 구성
  - 입력 시스템 및 시뮬레이션 제공
  - 손 추적 기능 지원
- **TextMesh Pro**: 고급 텍스트 렌더링 및 포맷팅
- **Animator**: 3D 모델 애니메이션 제어
- **Physics Engine**: 물리 기반 상호작용

---

## ✨ 주요 기능

### 1. 상호작용 인터페이스

#### 직접 조작 (Direct Manipulation)
- 사용자의 손을 인식하여 홀로그램을 터치하거나 잡는 **근거리 입력 모델** 구현
- 자연스러운 손 제스처를 통한 직관적인 상호작용

#### 공간 매핑 (Spatial Mapping)
- 현실 오브젝트를 스캔하여 가상 콘텐츠와 실제 환경 간의 **물리적 상호작용** 지원
- 실감 있는 AR/MR 환경 구성

### 2. 콘텐츠 시나리오

#### 정보 전달
- **TextMesh Pro** 를 통해 동물 실험의 정의 및 찬반 입장을 시각적으로 제시
- 교육적이고 균형 잡힌 정보 제공

#### 동적 연출
- **Animator** 를 활용해 토끼 모델의 상태 제어
  - **Idle**: 기본 대기 상태
  - **Run**: 움직이는 상태
  - **Dead**: 실험 후 상태
- 상황별 애니메이션 자동 출력

#### 이벤트 시스템
- 주사기(실험), 당근(상호작용) 오브젝트와 토끼 모델 간의 **충돌 감지** 구현
  - `Collision.cs`: 주사기 충돌 처리
  - `Collisioncarrot.cs`: 당근 충돌 처리
- 충돌 이벤트 기반 즉각적인 반응 시스템

---

## 🏗️ 시스템 구조

### Manager 시스템

```
Manager Script
├── index 변수: 버튼 클릭 횟수 추적
├── 단계별 진행 상황 관리
└── 사용자 상호작용에 따른 상태 전환
```

### 컴포넌트 구성

| 컴포넌트 | 역할 |
|----------|------|
| **Box Collider** | 충돌체 감지 및 물리 상호작용 |
| **Rigidbody** | 물리적 중력 효과 적용 |
| **NearInteractionGrabbable** | 손 조작을 통한 Grab 기능 활성화 |
| **Animator** | 3D 모델 상태 및 애니메이션 제어 |
| **TextMesh Pro** | UI 텍스트 렌더링 |

### 상호작용 흐름

```
사용자 입력
    ↓
MRTK 손 추적
    ↓
Collider 충돌 감지
    ↓
Event 발생 (Collision.cs / Collisioncarrot.cs)
    ↓
Animator 상태 변경
    ↓
콘텐츠 업데이트 (텍스트, 애니메이션 등)
```

---

## 📥 설치 및 사용 방법

### 필수 환경

- **Unity 2020 LTS** 이상
- **MRTK 2.8** 이상
- **Visual Studio 2019** 이상
- **Windows 10/11** SDK
- **HoloLens 2** 디바이스 또는 **HoloLens 에뮬레이터**

### 설치 단계

1. **저장소 클론**
   ```bash
   git clone https://github.com/rkdgml3577/AR_MR_Project.git
   cd AR_MR_Project
   ```

2. **Unity 프로젝트 열기**
   - Unity Hub에서 프로젝트 폴더 선택
   - 플랫폼을 **Universal Windows Platform (UWP)** 로 설정

3. **MRTK 설치**
   - Mixed Reality Toolkit 공식 설치 가이드 참고
   - 필수 패키지 설치

4. **빌드 및 배포**
   - File → Build Settings
   - Platform: **Universal Windows Platform** 선택
   - 대상 디바이스: **HoloLens** 선택
   - Build and Run

### 사용 방법

1. **HoloLens 2 착용**
2. 앱 실행 및 공간 매핑 확인
3. 손 제스처를 통한 홀로그램 상호작용
   - 손으로 오브젝트 잡기
   - 주사기 또는 당근으로 토끼와 상호작용
4. 단계별 시나리오 진행

---

## 🎓 기대 효과

### 교육적 가치

- **몰입형 학습 경험**: 텍스트 중심의 교육에서 벗어나 직접 체험을 통한 깊이 있는 학습
- **높은 관심도 및 참여도**: 최신 기술을 활용한 흥미로운 콘텐츠 제공
- **윤리적 이해도 증진**: 동물 실험의 필요성과 윤리적 문제를 균형 있게 이해

### 사회적 가치

- 과학 콘텐츠에 대한 **대중의 관심 제고**
- 기술과 교육의 융합을 통한 **혁신적 학습 방식** 제시

---

## 🚀 향후 계획

### 1단계: 고도화
- 현직자 수준의 **전문적인 체험** 구현
- 실제 동물 실험 프로세스 재현
- 더욱 상세한 과학적 정보 추가

### 2단계: 확장
- 다양한 실험 시나리오 개발
- 사용자 학습 데이터 분석 및 피드백 시스템
- 다양한 디바이스 지원 (AR 스마트폰, 웹 VR 등)

### 3단계: 커뮤니티
- 교육 기관 및 연구 기관과의 협력
- 오픈소스 기여 및 학술 논문 발표

---

## 📚 참고 자료

- [Unity Official Documentation](https://docs.unity3d.com/)
- [MRTK Official GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity)
- [AR Foundation Documentation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@latest)
- [HoloLens 2 Developer Guide](https://learn.microsoft.com/en-us/windows/mixed-reality/develop/advanced-concepts/using-the-hololens-shell)

---

## 📄 라이선스

이 프로젝트는 **2022-2학기 개별연구** 결과물입니다.  
학업 및 연구 목적으로의 사용을 권장합니다.

---

## 👨‍💻 작성자

- **개발자**: rkdgml3577
- **프로젝트**: AR/MR을 활용한 동물실험 관심 제고 콘텐츠 개발
- **기간**: 2022학년도 2학기
- **소속**: 컴퓨터과학 (CS)

---

## 📧 문의

프로젝트에 대한 질문이나 제안은 [GitHub Issues](https://github.com/rkdgml3577/AR_MR_Project/issues)를 통해 주시기 바랍니다.

---

**Last Updated**: 2026-05-09
