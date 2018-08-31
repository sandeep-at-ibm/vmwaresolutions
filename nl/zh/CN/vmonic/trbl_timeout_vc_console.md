---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-16"

---

# 连接到 VMware vSphere Web Client 时发生超时

## 问题
尝试连接到 vSphere Web Client 时，可能会收到以下超时错误：

`位于 <IP_address> 的服务器太长时间没有响应。`

## 解决方法
使用以下步骤来调查并解决问题。

1. 确保已完成将鼠标悬停在 **vCenter 控制台**按钮上时显示的工具提示中的步骤。为了方便起见，下面也列出了这些步骤：   
   1. 为浏览器安装 Adobe Flash Player 插件。   
   2. 在 {{site.data.keyword.slportal_full}} 中创建 VPN 密码。    
   3. 使用 {{site.data.keyword.cloud_notm}} 基础架构 VPN 凭证，登录到数据中心 VPN 门户网站。    
   4. 使用以下格式将 PSC (Platform Services Controller) 的 IP 地址和主机名映射添加到 hosts 文件中：

      ```javascript
      IPAddress              HostName
      ```

2. 记下显示的 IP 地址，因为在接下来的某个步骤中需要使用该地址。
3. 确保您有权访问 {{site.data.keyword.cloud_notm}} 基础架构 VPN。在 {{site.data.keyword.slportal}} 上完成以下步骤：
   1. 单击**帐户 > VPN 访问**。
   2. 单击 **VPN 访问**列中的 **SSL 链接**。
   3. 在 **username 的 VPN 访问**页面上，将**子网访问**选项设置为**手动**。
   4. 在同一页面上，找到该 IP 地址/主机名对的子网。有关更多信息，请参阅**步骤 2**。    

      例如，如果您的实例的 IP 地址为 `xx.yyy.zz.15`，并且 vCenter 的 IP 地址为 `xx.yyy.zz.10`，那么必须授予对子网 `xx.yyy.zz.0/26` 的访问权。

   5. 选中该子网的**授予访问权**复选框，然后单击**保存**。
