Geolocationの設定
================================================

WAFポリシーに保護されているアプリケーションに対して、Geolocation Enforcementを使用して特定の国でのアプリケーションの使用を制限または許可できます。
デフォルトでは、すべての地理位置からのアクセスが許可されます。Geolocation の設定を行うことで、接続される予定のない国からの接続をブロックすることが可能です。

CM画面左上部のworkspaceから、"Security"を選択します。 WAF > WAF Policysより、適用したいWAFポリシーを選択して、"General Settings"の設定ページを選択します。
“Advanced View”をEnableします。

   .. image:: images/Picture1.png
      :scale: 20%
      :align: center
   |

設定画面のAllowed Geolocations / Disallowed Geolocationsの指定により、ブロックしたい地理位置を設定して “Save & Deploy” します。

   .. image:: images/Picture2.png
      :scale: 30%
      :align: center
   |


その他、ポリシーの詳細カスタマイズ方法は以下の記事をご確認下さい。

- `Customize a WAF Policy <https://clouddocs.f5.com/bigip-next/latest/waf_management/#customize-a-waf-policy>`_
