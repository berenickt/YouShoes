# YouShoes
예담직업전문학교 프로젝트 수제화쇼핑몰
> 진행기간 : 2020.02.28~2020.04.01
>> JSP기반 웹 프로젝트

### 팀원
1. 유승우 - 프로필, 결제, 통계, 즐겨찾기, 공지사항 
2. 구교동 - 주문, 후기, 결제내역, 가게정보
3. 권우성 - 예약, 배송 
4. 배광준 - 로그인, 판매회원 관리, 구매자 메인 홈


### 개발 환경
1. HTML
2. CSS
3. JavaScript
4. BootStrap
5. jQuery
6. Ajax
7. Oracle -> MySQL
8. Tomcat 8.5


### 사용 API
1. 달력 API - FullCalendar
2. 통계 API - Chart.js
3. 지도 API - 카카오 지도 API
4. 결제 API - I'mport; (아임포트)  

### 프로시저 및 함수
* getimage(함수) - 작성자 : 유승우
  *이미지 갖고옴
<pre><code>
CREATE OR REPLACE FUNCTION GETIMAGE (
  P_SECTION IN VARCHAR2, 
  P_SECTION_NO IN NUMBER ) 
RETURN VARCHAR2
  IS
    v_getImage varchar2(50);
  BEGIN  
    select img_name 
    into v_getImage 
    from image img join image_detail imgd 
    on img.img_no = imgd.img_no 
    where section=P_SECTION and section_no = P_SECTION_NO and LIMIT 1;
  RETURN v_getImage;
END getimage;
</code></pre>

* pointupdate(프로시저) - 작성자 : 유승우
  *포인트 업데이트 
<pre><code>
create or replace PROCEDURE POINTUPDATE (
  P_no IN NUMBER , 
  P_CHARGEPOINT IN NUMBER ) AS
BEGIN
    update purchase_member 
    set point_now = point_now + p_chargepoint
    where pm_no= p_no;     
END POINTUPDATE;
</code></pre>

