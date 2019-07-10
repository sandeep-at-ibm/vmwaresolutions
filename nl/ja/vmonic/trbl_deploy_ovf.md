---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: troubleshooting, OVF deploy, how to deploy OVF file

subcollection: vmware-solutions


---

# VMware vSphere Web Client を使用した OVF ファイルのデプロイ
{: #trbl_deploy_ovf}

## 解決方法
{: #trbl_deploy_ovf-resolution}

vSphere Web Client を使用して OVF (Open Virtualization Format) ファイルをデプロイするには、次の手順を使用します。
1. OVF ファイルをデプロイする前に、`/etc/hosts` ファイルに以下のホスト情報を追加します。

   * Platform Services Controller (PSC) のホスト情報
   * VMware ESXi サーバーのホスト情報
   * vCenter のホスト情報
2. この情報が正常に追加されたことを `/etc/hosts` ファイルで確認します。 hosts ファイルは、例えば以下のリストのようになります。

    ```javascript
    10.131.9.201  psc-myinstance.myinstance.mydomain.com
    10.131.7.26   host0.myinstance.mydomain.com
    10.131.7.39   host1.myinstance.mydomain.com
    10.131.7.6    host2.myinstance.mydomain.com
    10.131.7.48   host3.myinstance.mydomain.com
    10.131.9.196  vcenter-1.myinstance.mydomain.com
    ```
3. {{site.data.keyword.slportal_full}}で、必要な VPN (仮想プライベート・ネットワーク) すべてにアクセスできることを確認します。 この例では、`10.131.7.xx` と `10.131.9.xxx` になります。
4. データ・センター用の VPN にサインインします。
5. **「vCenter」**をクリックして vSphere Web Client にアクセスします。
6. ホストを右クリックして、`.ovf` ファイルをデプロイします。
