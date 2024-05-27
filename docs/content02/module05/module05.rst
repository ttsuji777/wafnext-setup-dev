Geolocationの設定
================================================

WAFポリシーによって保護されているアプリケーションに対して、Geolocation Enforcementを使用して、特定の国でのアプリケーションの使用を制限または許可することができます。 
デフォルトでは、すべての国からのアクセスが許可されます。Geolocationの設定を行うことによって、特定の国からの接続をブロックすることが可能です。

CM画面左上部のworkspaceから、"Security"を選択します。

”WAF” > “Policies”で、作成済みのWAFポリシーを選択し、"General Settings"の設定ページを開きます。
Geolocationの設定を表示するために“Advanced View”のトグルをクリックし、有効にします。

   .. image:: images/Picture1.png
      :scale: 20%
      :align: center
   |


設定画面の”Allowed Geolocations”および”Disallowed Geolocations”を指定して、接続を許可および拒否したい国を選択して、“Save & Deploy”をクリックします。

   .. image:: images/Picture2.png
      :scale: 30%
      :align: center
   |


その他、ポリシーの詳細カスタマイズ方法は以下の記事をご確認下さい。

- `Customize a WAF Policy <https://clouddocs.f5.com/bigip-next/latest/waf_management/#customize-a-waf-policy>`_
