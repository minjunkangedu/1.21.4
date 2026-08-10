# Void Hunt · AR Shades  (Fabric 1.21.4)

보이드 AR 선글라스를 **머리에 쓰면** 자동으로 가장 가까운 적을 락온하고,
사거리 안이면 자동으로 공격하는 **헌팅 HUD** 모드입니다.

## 기능
- **선글라스 아이템**: 머리 슬롯에 착용하는 3D 모델 (`voidhunt:void_shades`)
- **자동 타겟**: 반경 16칸 내 가장 가까운 적대적 몹(좀비/스켈레톤 등) 락온
- **자동 공격**: 타겟이 근접 사거리(≈3칸) 안이고 공격 게이지가 다 차면 자동 타격
- **HUD 오버레이**: HUNT 상태, 타겟 이름/HP/거리, 중앙 락온 브래킷
- **토글 키**: 기본 `H` (선글라스를 써야 실제로 작동)

값 조정은 `src/main/java/com/voidhunt/VoidHuntClient.java` 상단
`RANGE`(탐지 반경) · `REACH`(공격 사거리) 상수에서 바꾸면 됩니다.

## 빌드 (jar 만들기)  ※ 클라우드에서 못 뽑아 소스로 드립니다
필요: **JDK 21**

```bash
# 프로젝트 폴더에서
gradle wrapper --gradle-version 8.10   # (최초 1회, gradlew 생성)
./gradlew build                        # Windows: gradlew.bat build
```
- 결과물: `build/libs/voidhunt-1.0.0.jar`
- IntelliJ IDEA로 폴더를 열면 자동으로 임포트되어 Gradle 탭 → build 로도 됩니다.

## 설치
1. **Fabric Loader** 설치된 1.21.4 클라이언트 준비
2. `.minecraft/mods` 폴더에 넣기:
   - 방금 만든 `voidhunt-1.0.0.jar`
   - **Fabric API** jar (필수, modrinth/curseforge에서 1.21.4용 다운로드)
3. 게임 실행

## 사용
- 아이템 지급(크리에이티브/OP): `/give @s voidhunt:void_shades`
  (또는 크리에이티브 전투 탭에 있음)
- 들고 **우클릭** → 머리에 착용
- 착용 상태에서 자동으로 락온+자동공격. `H`로 헌트모드 on/off.

## 주의
- 자동 공격은 사실상 **킬어라(자동 조준 타격)** 입니다.
  싱글/친구 서버에선 문제없지만, **안티치트가 있는 공개 서버에선 차단/밴 위험**이 있어요.
  공개 서버에서 쓰기 전 규칙을 확인하세요.
- Bedrock(통합판) 미지원.

## 버전이 안 맞아 빌드가 실패하면
`gradle.properties`의 버전이 최신과 다를 수 있습니다. 가장 확실한 방법:
1. https://fabricmc.net/develop 에서 1.21.4용
   loader / yarn / fabric-api / loom 버전을 확인해 `gradle.properties`·`build.gradle`에 반영
2. 혹은 공식 템플릿(https://fabricmc.net/develop/template/)으로 1.21.4 빈 프로젝트를 만든 뒤
   이 프로젝트의 `src/` 폴더를 통째로 복사해 넣기
드물게 특정 심볼(API 이름)이 안 잡히면 알려주세요 — 해당 부분만 맞춰 드릴게요.
