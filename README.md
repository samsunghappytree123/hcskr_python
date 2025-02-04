# HCSKR📱

[![Send mail](https://img.shields.io/badge/-support@leok.kr-63d863?style=flat-square&logo=gmail&logoColor=white&link=mailto:support@leok.kr)](mailto:support@leok.kr) [![Badge](https://img.shields.io/pypi/v/hcskr?label=Version&style=flat-square)](https://pypi.org/project/hcskr/) [![Send mail](https://img.shields.io/pypi/dm/hcskr?color=orange&label=Downloads&style=flat-square)](https://pypi.org/project/hcskr/) [![Licence](https://img.shields.io/pypi/l/hcskr?label=License&style=flat-square)](https://github.com/331leo/hcskr_python/blob/main/LICENSE) [![Badge](https://img.shields.io/pypi/status/hcskr?color=%230099ff&label=Status&style=flat-square)]() <br>
파이썬용 학생 코로나 자가진단 라이브러리 입니다. <br>
**정상 작동을 위해 1.13.0이상으로 업그레이드 해주세요.<br>**
**버전 1.13.0: 7/31 자가진단 보안강화 관련 패치**

- https://pypi.org/project/hcskr/
- https://github.com/331leo/hcskr_python
- https://github.com/331leo/hcs_api_readme (API분석 시트)

## 📥다운로드

**이 모듈은 파이썬 3.8 ~ 3.10 까지의 동작을 보장합니다.
이외의 버전에서는 제대로 작동하지 않을 수 있습니다.**

윈도우나 리눅스의 터미널에서 다음과 같이 입력합니다.

```shell
pip install hcskr
```

오류가 나는 경우, `python -m pip install --upgrade pip` 로 pip를 업데이트 해주세요.

## 🤖사용법

자가진단 서버와 통신하기 기능이기 때문에, 비동기 처리를 추천드립니다.

```python
#동기 처리
import hcskr
hcskr.selfcheck("홍길동","030510","서울","두둥실고","고등학교","1234")

#hcskr.selfcheck("이름","생년월일","지역","학교이름","학교종류","비밀번호(숫자4자리)")
#kwargs도 지원합니다 hcskr.selfcheck(birth="생년월일",schoolname="학교이름",area="서울",name="홍길동",level="중학교",password="1234")
```

```python
#비동기 처리
import asyncio
import hcskr
async def main():
    await hcskr.asyncSelfCheck("이름","생년월일","지역","학교이름","학교종류","비밀번호(숫자4자리)")
asyncio.get_event_loop().run_until_complete(main())
```

<details><summary>▶️지원하는 모든 지역이름 보기</summary>
<p>
지원하는 지역 이름은 다음과 같습니다:

'서울', '서울시', '서울교육청', '서울시교육청', '서울특별시'</br>
'부산', '부산광역시', '부산시', '부산교육청', '부산광역시교육청'</br>
'대구', '대구광역시', '대구시', '대구교육청', '대구광역시교육청'</br>
'인천', '인천광역시', '인천시', '인천교육청', '인천광역시교육청'</br>
'광주', '광주광역시', '광주시', '광주교육청', '광주광역시교육청'</br>
'대전', '대전광역시', '대전시', '대전교육청', '대전광역시교육청'</br>
'울산', '울산광역시', '울산시', '울산교육청', '울산광역시교육청'</br>
'세종', '세종특별시', '세종시', '세종교육청', '세종특별자치시', '세종특별자치시교육청'</br>
'경기', '경기도', '경기교육청', '경기도교육청'</br>
'강원', '강원도', '강원교육청', '강원도교육청'</br>
'충북', '충청북도', '충북교육청', '충청북도교육청'</br>
'충남', '충청남도', '충남교육청', '충청남도교육청'</br>
'전북', '전라북도', '전북교육청', '전라북도교육청'</br>
'전남', '전라남도', '전남교육청', '전라남도교육청'</br>
'경북', '경상북도', '경북교육청', '경상북도교육청'</br>
'경남', '경상남도', '경남교육청', '경상남도교육청'</br>
'제주', '제주도', '제주특별자치시', '제주교육청', '제주도교육청', '제주특별자치시교육청', '제주특별자치도'

</p>
</details>

<details><summary>▶️지원하는 모든 학교종류 보기</summary>
<p>
지원하는 학교급 이름은 다음과 같습니다:

'유치원', '유','유치'</br>
'초등학교', '초','초등'</br>
'중학교', '중','중등'</br>
'고등학교', '고','고등'</br>
'특수학교', '특','특수','특별'

</p>
</details>

## 🔒더 많은 기능

개인정보 보호를 위해, 사용자의 정보를 보관해야 하는 경우 개인정보를 토큰화 하는 기능을 제공합니다.</br>
토큰의 만료 기한은 없으니, 자가진단 정보 저장이 필요한 경우 토큰화 한후 저장하는것을 추천드립니다. </br>
추가적으로, 토큰 생성도 자가진단 서버와 통신하기 때문에, 비동기 처리를 추천드립니다.

> 토큰 생성
>
> ```python
> #동기 처리
> import hcskr
> result = hcskr.generatetoken("이름","생년월일","지역","학교이름","학교종류","비밀번호(숫자4자리)") #리턴값 참고하세요
>
> #비동기 처리
> import asyncio
> import hcskr
> async def main():
>   result = await hcskr.asyncGenerateToken("이름","생년월일","지역","학교이름","학교종류","비밀번호(숫자4자리)") #리턴값 참고하세요
>
> asyncio.get_event_loop().run_until_complete(main())
> ```

> 토큰으로 자가진단
>
> ```python
> #동기 처리
> import hcskr
> hcskr.tokenselfcheck("위에서 생성한 토큰")
>
> #비동기 처리
> import asyncio
> import hcskr
> async def main():
>   await hcskr.asyncTokenSelfCheck("위에서 생성한 토큰")
> asyncio.get_event_loop().run_until_complete(main())
> ```

> 비밀번호 변경
>
> ```python
> #동기처리
> import hcskr
> hcskr.changePassword("이름","생년월일","지역","학교이름","학교종류","현재 비밀번호(숫자4자리)", "변경할 비밀번호(숫자4자리)")
>
> #비동기 처리
> import asyncio
> import hcskr
> async def main():
>   await hcskr.asyncChangePassword("이름","생년월일","지역","학교이름","학교종류","현재 비밀번호(숫자4자리)","변경할 비밀번호(숫자4자리)")
> asyncio.get_event_loop().run_until_complete(main())
> ```

## ↩️리턴값

모든 리턴값은 Dict 로 반환됩니다.</br>
리턴값 구조는 다음과 같습니다: </br>

```python
{"error":Boolen(True,False),"code":"처리코드(밑의 처리코드 종류 참조)","message":"해당 에러나, 성공 상황에 대한 설명",......}
#토큰생성일 경우 'token':토큰 이 추가됩니다
```

<details><summary>▶️처리코드 종류</summary>
성공 = "SUCCESS"</br>  
존재하지 않는 지역, 학교급 = "FORMET"</br>  
학교 검색 실패 = "NOSCHOOL"</br>  
학생 검색 실패 = "NOSTUDENT"</br>
비밀번호에러 = "PASSWORD"</br>  
알 수 없는 에러 = "UNKNOWN" </br>
올바르지 않은 토큰 = "WRONGTOKEN"
</details>

## 💡 TIP

- 리턴값의 `'code'` 를 이용하시면 성공, 실패여부, 실패이유를 모두 알 수 있어요!</br>
  또한 `'message'`로 이용자에게 바로 실패이유를 알릴수도 있어요!
- 선택 파라미터로 `customloginname` 을 입력하면, 수행자 이름을 바꿀수 있어요!

```python
hcskr.selfcheck("이름","생년월일","지역","학교이름","학교종류","비밀번호(숫자4자리)", "커스텀수행자")
```

![screenshot](./img/screenshot.jpg)
