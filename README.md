# Auth Module

Spring Boot 기반의 인증·인가 모듈을 하나의 JAR로 제공하는 프로젝트입니다.

---

## 🚀 기술 스택

| |                    |
|:------:|:-----------------------|
| ☕️     | Java 17+               |
| 🌱     | Spring Boot            |
| 🔒     | Spring Security        |
| 🔑     | OAuth2 Client          |
| 🛡️     | JWT (JSON Web Token)   |
| 🗄️     | Redis                  |
| 📜     | Swagger / OpenAPI      |
| 📦     | Gradle                 |
| 🧩     | Modular Configuration  |

---

## 🎯 프로젝트 개요

- **단일 모듈**: 하나의 `auth-starter` JAR에 모든 기능을 포함  
- **개요**  
  - 일반 로그인/회원가입 API  
  - OAuth2 소셜 로그인 연동 (Kakao, Google, Naver 등)  
  - JWT Access & Refresh Token + Redis 저장소 관리  
  - Swagger/OpenAPI 문서 자동화  
  - `@EnableAuthModule` 애너테이션으로 간편 활성화  

---

## 🔗 다른 프로젝트에서 모듈로서 재사용하는 방법법

### 1. 원격 Maven/Gradle 저장소에 배포 후 사용

`auth-starter`를 Maven Central, 사내 Nexus/Artifactory 등에 배포한 뒤에, 소비 프로젝트의 `build.gradle`에 아래와 같이 추가합니다:

```groovy
repositories {
    mavenCentral()          // 또는 사내 레포
}

dependencies {
    implementation 'com.mycompany.auth:auth-starter:1.0.0'
}
```

### 2. 로컬 Composite Build 사용

로컬에서 소스 코드를 함께 관리하며 사용하려면 소비 프로젝트의 `settings.gradle`에 다음을 추가:

```groovy
// 소비 프로젝트 settings.gradle
includeBuild '/path/to/auth-starter'
```

이후 소비 프로젝트 `build.gradle`에는 평소와 같이:

```groovy
dependencies {
    implementation 'com.mycompany.auth:auth-starter'
}
```

를 선언하면, 로컬 빌드 결과를 참조합니다.

---

## 📦 주요 컴포넌트

```text
com.mycompany.auth
├── annotation
│   └── EnableAuthModule.java
├── config
│   └── AuthAutoConfiguration.java
├── props
│   └── AuthProperties.java
├── jwt
│   ├── JwtTokenProvider.java
│   └── JwtAuthenticationFilter.java
├── redis
│   └── RedisTokenStore.java
├── user
│   ├── UserPrincipal.java
│   ├── UserDetailsService.java
│   └── DefaultUserDetailsService.java
└── oauth
    └── OAuth2SuccessHandler.java
```

---

## 📅 마일스톤

1. 프로젝트 환경 설정 및 Gradle 빌드  
2. JWT 및 Redis 토큰 관리 구현  
3. OAuth2 소셜 로그인 연동  
4. UserDetailsService 확장성 확보  
5. Swagger/OpenAPI 문서화  
6. 테스트 & 배포 준비  

---
