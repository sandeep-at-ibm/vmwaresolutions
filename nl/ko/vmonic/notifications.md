---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# 시스템 알림 관리

시스템 또는 사용자 오퍼레이션의 상태에 대한 알림을 확인할 수 있습니다. 또한 정보를 사용하여 발생할 수 있는 문제점을 진단하고 해결할 수도 있습니다.

## 알림 보기

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **알림**을 클릭하십시오.
2. **알림 히스토리** 테이블에서 모든 알림에 대한 요약을 보십시오.

   표 1. 알림 히스토리

    <table>
      <tr>
        <th>열</th>
        <th>설명</th>
      </tr>
      <tr>
        <td>심각도</td>
        <td>알림으로 보고된 이벤트의 심각도입니다.
          <dl class="dl">
          <dt class="dt dlterm">위험</dt>
          <dd class="dd">심각한 이벤트는 전체 시스템 또는 서비스에 영향을 줄 수 있습니다.</dd>
          <dt class="dt dlterm">오류</dt>
          <dd class="dd">관리자 또는 사용자의 개입이 필요할 수 있는 오퍼레이션 중에 오류 이벤트가 발생합니다. </dd>
          <dt class="dt dlterm">경고</dt>
          <dd class="dd">컴포넌트가 실패했거나 올바르게 작동하지 않습니다. 그러나 실패로 인해 컴포넌트의 지속적인 프로세스가 중단되지 않습니다.</dd>
            <dt class="dt dlterm">정보용</dt>
            <dd class="dd">시스템 또는 사용자 오퍼레이션이 완료되었습니다. 일반적으로 다음 이벤트가 정보용 알림을 보고합니다.
              <ul class="ul">
                <li class="li">서비스가 설치됩니다.</li>
                <li class="li">서비스가 업그레이드됩니다.</li>
                <li class="li">서비스가 제거됩니다.</li>
                <li class="li">모든 서비스가 추가된 ESXi 서버에 대해 다시 구성됩니다.</li>
                <li class="li">모든 서비스가 제거된 ESXi 서버에 대해 다시 구성됩니다.</li>
              </ul>
            </dd>
          </dl>
        </td>
       </tr>
       <tr>
         <td>유형</td>
         <td>보고된 이벤트가 관련된 컴포넌트의 유형입니다.<ul><li>vCenter Server 인스턴스</li><li>Cloud Foundation 인스턴스</li><li>서비스</li><li>시스템</li></ul></td>
       </tr>
       <tr>
         <td>리소스</td>
         <td>알림을 전송하는 인스턴스 또는 서비스의 이름입니다.</td>
       </tr>
       <tr>
         <td>설명</td>
         <td>알림에 대한 간단한 설명입니다.</td>
       </tr>
       <tr>
         <td>날짜</td>
         <td>알림이 전송된 날짜 및 시간입니다.</td>
       </tr>
    </table>                                       

3. 알림 행을 클릭하여 알림의 세부사항을 보십시오.

## 알림 필터링

기본적으로 읽지 않은 모든 알림이 표시됩니다. 상태, 심각도 및 유형별로 알림을 필터링할 수 있습니다. 알림을 필터링하려면 **상태**, **심각도** 또는 **유형** 드롭 다운 목록에서 표시할 항목에 대해서만 선택란을 선택하십시오.

### 관련 링크

* [FAQ](faq.html)
* [사용자 계정 및 설정](useraccount.html)
