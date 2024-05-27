セキュリティイベントの確認とシグネチャのチューニング
================================================

誤検知などが発生した場合の対処例をご紹介します。
以下で実施する内容は、Webアプリケーションの各パラメータの役割が全て把握できている場合を除き、運用開始前から全てを設定するのは難しいかもしれません。その場合は、仮運用・本運用に入ってから、チューニングが簡単に実施可能です。

CM画面左上部のworkspaceから、”Security”を選択します。
“WAF Dashboards”からセキュリティモニタリング情報を確認します。
“Polices”からポリシーごとにセキュリティイベントに対してフィルターかけます。

   .. image:: images/Picture1.png
      :scale: 30%
      :align: center
   |

“Signatures”から先ほどrejectされたsql injectionリクエストをクリックし、”View Log”から詳細logを確認可能です。
(クライアントPCのブラウザ上のリスポンスから表記されたSupportIDをlog中のSupportIDを比較することでイベントログを特定出来ます。) 


   .. figure:: images/Picture2.png
      :scale: 20%
      :align: center
   |

   .. image:: images/Picture3.png
      :scale: 30%
      :align: center
   |

“Actions”をクリックすると、シグネチャごとでenforcement settingを特定ポリシーに対してoverrideすることが出来ます。

   .. image:: images/Picture4.png
      :scale: 30%
      :align: center
   |

“Save” > “Deploy” でシグネチャのoverrideを適用して、クライアントから再度SQLインジェクション攻撃をする際、リクエストはrejectされません。


   .. figure:: images/Picture5.png
      :align: center
   |

また、Event Logsからはリクエストログを確認出来ます。

   .. figure:: images/Picture6.png
      :align: center
   |
