Blocking画面のカスタマイズ
================================================

攻撃をブロックした際、ユーザに返されるレスポンスページの内容をカスタマイズすることが可能です。

CM画面左上部のworkspaceから、"Security"を選択します。
WAF > WAF Policysより、適用したいWAFポリシーを選択して、"Response Pages"の設定ページを選択します。

Response Bodyでブロックページの内容をカスタマイズすることが出来ます。
"Preview"をクリックすることで、ブロックページのレビューが表示されます。クライアントから攻撃を行う際、カスタマイズされた内容がブラウザで表示されます。


   .. image:: images/Picture1.png
      :scale: 20%
      :align: center
   |

   .. image:: images/Picture2.png
      :align: center
   |


また、必要に応じて、Response Headersをカスタマイズする（eg. response codeを200から403へ変更など）や、ブロックページを指定URLへRedirectすることも設定可能です。

   .. image:: images/Picture3.png
      :scale: 20%
      :align: center
   |

   .. image:: images/Picture4.png
      :scale: 20%
      :align: center
   |
