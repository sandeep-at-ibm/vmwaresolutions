---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# ESXi サーバーの追加操作が失敗すると Cloud Foundation インスタンスを更新できない
{: #trbl_cfupdatesfail}

## 問題
{: #trbl_cfupdatesfail-problem}

ESXi サーバーを V1.5 または V1.6 の VMware Cloud Foundation インスタンスに追加し、その追加操作が失敗した場合は、更新オプションが無効になり、V1.5 から V1.6 または V1.6 から V1.7 への更新をインスタンスに適用することはできません。

## 解決方法
{: #trbl_cfupdatesfail-resolution}

V1.5 Cloud Foundation インスタンスに V1.6 更新、または V1.6 インスタンスに V1.7 更新を適用する前に、ESXi サーバーの追加操作が正常に完了したことを確認してください。
