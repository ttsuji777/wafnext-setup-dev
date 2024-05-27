Blocking画面のカスタマイズ
================================================

攻撃をブロックした際、ユーザに返されるレスポンスページの内容をカスタマイズすることが可能です。

CM画面左上部のworkspaceから、"Security"を選択します。
”WAF” > “Policies”で、作成済みのWAFポリシーを選択し、"Response Pages"をクリックして、レスポンスページの設定ページを選択します。

”Response Body”で、ブロックページの内容をカスタマイズすることができます。 "Preview"をクリックすることで、ブロックページのレビューが表示されます。
クライアントから攻撃があった際に、カスタマイズされた内容がブラウザに表示されます。

例えば、デフォルトでは” The requested URL was rejected.”と表示されるメッセージ部分を”Blocking!!!”と変更する場合には、以下の画面のようになります。


   .. image:: images/Picture1.png
      :scale: 20%
      :align: center
   |

   .. image:: images/Picture2.png
      :align: center
   |


”Response Headers”タブをクリックすると、レスポンスヘッダをカスタマイズする (例: Response Codeを”200”から”403”へ変更)ことができます。

   .. image:: images/Picture3.png
      :scale: 20%
      :align: center
   |


また、”Blocking Page”タブで”Response Type”を”Redirect URL”に設定すると、ブロックページを指定したURLへリダイレクトすることも可能です。

   .. image:: images/Picture4.png
      :scale: 20%
      :align: center
   |
