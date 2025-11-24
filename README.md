TripleK는 C# WinForms로 개발된 카페 키오스크 애플리케이션입니다. TCP 소켓 통신을 기반으로 서버와 연동하여 상품 주문, 결제 및 관리자 기능을 통한 재고 관리를 수행합니다.

📋 프로젝트 개요
플랫폼: Windows Forms Application (.NET Framework 4.7.2)

언어: C#

통신 방식: TCP/IP Socket Communication (JSON 직렬화 사용)

UI 라이브러리: MaterialSkin 2, Bunifu UI WinForms

✨ 주요 기능
1. 사용자 모드 (키오스크)
카테고리별 메뉴 조회: 커피, 음료, 디저트, 케이크 탭으로 구분하여 메뉴를 표시합니다.

장바구니 기능: MenuItemControl을 통해 상품을 담거나 수량을 조절할 수 있습니다.

실시간 금액 계산: 장바구니에 담긴 상품의 총액을 실시간으로 표시합니다.

주문 및 결제: 서버와 통신하여 주문(BuyItems)을 처리하고 결과를 반환받습니다.

2. 관리자 모드 (Admin)
히든 접근 방식: 메인 화면의 '커피' 버튼을 5회 연속 클릭하면 관리자 로그인 창이 활성화됩니다.

보안: 비밀번호 인증 후 접근 가능합니다. (기본 비밀번호: aa)

상품 관리:

상품 추가: 이미지, 가격, 초기 수량을 설정하여 새 메뉴를 등록합니다.

상품 수정/삭제: 기존 메뉴의 정보를 수정하거나 삭제할 수 있습니다.

재고 관리: 서버와 동기화된 현재 재고를 확인하고 추가 입고(AddStock)를 처리합니다.

3. 네트워크 (Client)
서버(127.0.0.1:8000)와 연결하여 데이터를 주고받습니다.

주요 통신 명령어(Instructions Enum):

GetItemDetail: 상품 정보 및 재고 조회

BuyItems: 상품 구매

AddAmount: 재고 추가

AddProduct / DeleteProduct: 상품 등록 및 삭제

🛠 설치 및 실행 방법
필수 요건:

Visual Studio 2019 이상

.NET Framework 4.7.2

NuGet 패키지 복원 (MaterialSkin, System.Text.Json 등)

서버 구동:

이 클라이언트는 서버와 통신해야 정상 작동합니다. (서버 프로젝트는 별도 경로 ../Server/Server.csproj에 위치하는 것으로 보임)

서버가 127.0.0.1 포트 8000에서 실행 중이어야 합니다.

실행:

TripleK.sln 솔루션 파일을 엽니다.

Build 후 MainForm을 시작 프로젝트로 설정하여 실행합니다.

📂 소스 코드 구조
MainForm.cs: 프로그램의 진입점이자 메인 키오스크 화면.

Client.cs (TKClient): TCP TcpClient와 StreamReader/Writer를 이용한 통신 로직 구현.

AdminForm.cs: 상품 추가/수정/삭제 및 재고 관리를 위한 관리자 UI.

Cart.cs & PayForm.cs: 장바구니 확인 및 결제 프로세스 처리.

MenuItemControl.cs: 메뉴 아이템을 표시하기 위한 사용자 정의 컨트롤 (UserControl).

PassWordForm.cs: 관리자 모드 진입을 위한 비밀번호 입력 창.

📦 사용된 패키지 (NuGet)

System.Text.Json: 서버 통신 간 JSON 데이터 직렬화/역직렬화

System.Threading.Tasks.Extensions: 비동기 처리 지원
