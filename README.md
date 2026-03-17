Smart Wallpad System (Home Assistant 기반 IoT 출입 관리 시스템)
📌 프로젝트 개요

Raspberry Pi와 7" 터치 디스플레이를 활용하여
Home Assistant 기반의 Wallpad(월패드) 시스템을 구현한 프로젝트입니다.

STM32 및 Arduino 보드를 통해 센서 및 제어 데이터를 수집하고,
이를 MQTT, MariaDB와 연동하여 출입 관리 및 스마트 홈 제어 시스템을 구축했습니다.

🎯 프로젝트 목표

Raspberry Pi + Touch Display 기반 Wallpad UI 구현

STM32 / Arduino를 통한 센서 및 제어 시스템 구축

MQTT + MariaDB 기반 데이터 통합 및 로그 관리

👨‍💻 담당 역할

STM32 보드에 버튼, 부저, 서보모터, LED 연결 및 Raspberry Pi 연동

Flask 기반 실시간 웹캠 스트리밍 및 캡처 시스템 구현

초인종 / 문열림 이벤트 MariaDB 저장

Home Assistant UI에 날짜, 시간, 날씨 표시

🎥 시연 영상

👉 https://youtu.be/M8JA2rLNz2I?si=XrtbHMHnrbMkMU0O

🖥️ UI 화면

(이미지 추가 예정)

⚙️ 주요 기능
🅰️ 제어 및 알림 (STM32)

물리 버튼 + 부저를 이용한 초인종 기능

서보 모터를 이용한 문 열림/닫힘 제어

사용자 요청 기반 실시간 캡처 (Home Assistant 저장)

구역별 LED 제어 (거실 / 안방 / 2층 등)

🅱️ 보안 및 인증 (Arduino)

RFID 기반 사용자 인증

태그 시 재실 상태 (집 / 외출) 자동 토글

LED 및 서보모터를 통한 시각적 피드백 제공

🅲 모니터링 및 허브 (Raspberry Pi)

터치 디스플레이 기반 중앙 제어 대시보드

Flask 기반 실시간 웹캠 스트리밍

Bridge 서버

Serial(STM32/Arduino) → MQTT 변환

Home Assistant 연동

MariaDB

출입 로그 및 이벤트 기록

🏗️ 시스템 아키텍처

(아키텍처 이미지 추가)

🗄️ Database (MariaDB)
Tables

rfid_log : 사용자 재실 상태(집/외출) 기록

door_bell : 초인종 이벤트 기록

door_lock : 도어락 상태(OPEN/CLOSE) 기록

📂 프로젝트 구조
├── cam_server.py
│   └── Flask 기반 웹캠 스트리밍 및 스냅샷 서버
│
├── bridge.py
│   └── Serial ↔ MQTT ↔ MariaDB ↔ Home Assistant 브릿지
│
├── homeassistant/
│   ├── configuration.yaml
│   └── automations.yaml
│
├── firmware/
│   ├── STM32/
│   └── Arduino/
│
└── database/
    └── MariaDB
🔧 기술 스택

Hardware

Raspberry Pi 4

STM32

Arduino Uno

RFID Module, Servo Motor, LED, Buzzer

Software

Python (Flask)

Home Assistant

MQTT

MariaDB

⚡ 데이터 흐름

STM32 / Arduino → Serial → Raspberry Pi

bridge.py → MQTT → Home Assistant

Home Assistant → 자동화 처리

이벤트 → MariaDB 저장

사용자 → UI (Touch Display)로 제어

🚧 문제 해결 경험
❗ Issue

PC 기반 Qt 환경과 Raspberry Pi 터치스크린 간
버전 불일치로 인해 의존성 문제가 발생

✅ Solution

Home Assistant 기반의 중앙 집중형 아키텍처로 전환

🎯 Result

장치 간 호환성 문제 해결

터치스크린 + 모바일 모두에서 접근 가능한 UI 구축

시스템 확장성 및 유지보수성 향상
