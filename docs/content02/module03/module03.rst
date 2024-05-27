セキュリティイベントの確認とシグネチャのチューニング
================================================

誤検知などが発生した場合の対処例をご紹介します。
以下で実施する内容は、Webアプリケーションの各パラメータの役割が全て把握できている場合を除き、運用開始前から全てを設定するのは難しいかもしれません。その場合でも、仮運用・本運用に入ってからのチューニングは、簡単に実施可能です。

CM画面左上部のworkspaceから、”Security”を選択します。
“WAF Dashboards”からセキュリティモニタリング情報を確認します。
“Polices”から、ポリシー単位でセキュリティイベントに対してフィルターをかけます。

   .. image:: images/Picture1.png
      :scale: 30%
      :align: center
   |

“Signatures”から、先ほどrejectされたSQLインジェクションのリクエストである 「((200015125) SQL-INJ in "id"」をクリックし、”View Logs”から詳細なログを確認できます。
クライアントPCのブラウザでレスポンスとして表示されたSupport IDと、ログ中のSupport IDを比較することで、イベントログを特定することができます。

   .. figure:: images/Picture2.png
      :scale: 20%
      :align: center
   |

   .. figure:: images/Picture3.png
      :scale: 20%
      :align: center
   |
   .. image:: images/Picture4.png
      :scale: 30%
      :align: center
   |

“Signatures”から、先ほどrejectされたSQLインジェクションのリクエストをクリックし、“Actions”をクリックすると、シグネチャ単位でEnforcement設定を特定ポリシーに対して上書きすることができます。

ここでは、先ほどブロックされたシグネチャのEnforcement Settingを”Stage”、つまりブロックしない設定に変更し、作成済みのWAFポリシーに適用します。設定後、”Save & Deploy”をクリックして、変更を反映します。

   .. image:: images/Picture5.png
      :scale: 30%
      :align: center
   |

“Deploy latest changes?”の画面で必要に応じてコメントを追記して、”Deploy”をクリックします。

   .. image:: images/Picture6.png
      :scale: 25%
      :align: center
   |

画面上部に“Deploy completed successfully.”と表示されたら、”Cancel & Exit”をクリックして設定を終了します。

   .. image:: images/Picture7.png
      :scale: 50%
      :align: center
   |


2.1で実施したSQLインジェクション攻撃を、再度実行します。WindowsクライアントにログインしてChromeブラウザを開き、DVWAのSQL Injectionページより、User ID に 'or 1=1 # と入力して、SQLインジェクション攻撃を実行します。
今回は該当のシグネチャに対して”Enforcement設定が”Stage”となっているため、攻撃はrejectされず、ユーザー情報を取得できます。


   .. figure:: images/Picture8.png
      :scale: 50%
      :align: center
   |

また、Event Logsからリクエストログを確認することができます。ブロックされなかったリクエストを表示するには、”画面右上の”Show Filter”をクリックし、”Clear All”をクリックしてフィルタを削除します。

   .. figure:: images/Picture9.png
      :scale: 30%
      :align: center
   |
