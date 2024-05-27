WAFポリシーを作成してアプリケーションへ適用
=========================================================

Central Manager (CM)画面左上部のworkspace (3x3のドット)から、”Security”を選択します。

   .. image:: images/Picture1.png
      :scale: 15%
      :align: center
   |

画面左側で"WAF" > "Policies"を選択、"Create"をクリックしてポリシーを新規作成します。

   .. image:: images/Picture2.png
      :scale: 50%
      :align: center
   |

- Name:
   - **dvwa_waf_policy**　（任意の名前）

- テンプレートを選択するため、”Advanced View”のトグルをクリックし、有効にします。

- Template:
   - **RAPID-Template**

- Enforcement Mode:
   - **Blocking**

- “Save” をクリックします

   .. image:: images/Picture3.png
      :scale: 30%
      :align: center
   |

作成されたWAFポリシーを選択し、”General Settings”から”Log Events”を”All”にして、”Save”をクリックします。

   .. image:: images/Picture4.png
      :scale: 15%
      :align: center
   |

   .. image:: images/Picture5.png
      :scale: 15%
      :align: center
   |

"Attack Signatures"のページを選択し、"Enforce" > "Enforce all Staged Signatures"でシグネチャのstagingを解除します。

   .. image:: images/Picture6.png
      :scale: 15%
      :align: center
   |

   .. image:: images/Picture7.png
      :scale: 15%
      :align: center
   |

シグネチャのステータスが”Enforced”になっていることを確認したら、”Cancel”をクリックして、WAFポリシー画面に戻ります。

Central Manager画面左上部のworkspaceから、"Applications"へ戻ります。先ほど作成したアプリケーション (HTTP-DVWA)を選択し、"Edit"をクリックします。

   .. image:: images/Picture8.png
      :scale: 20%
      :align: center
   |

   .. image:: images/Picture9.png
      :scale: 20%
      :align: center
   |


“Security Policies”の編集マークをクリックします。

   .. image:: images/Picture10.png
      :scale: 20%
      :align: center
   |

- “Use a WAF Policy”のトグルをクリックして、有効にします。

- WAF Policy Name:
   - **dvwa_waf_policy** (先ほど作成したWAFポリシー)

- “Save” をクリックします

- “Review & Deploy” > “Validate All” > “Deploy Changes” でWAFポリシーをアプリケーションへ適用します

   .. image:: images/Picture11.png
      :scale: 20%
      :align: center
   |


作成済みのアプリケーション (“HTTP-DVWA”)にWAFポリシーが適用されていることを確認します。

   .. image:: images/Picture12.png
      :scale: 20%
      :align: center
   |

2.1で実施したSQLインジェクション攻撃を、再度実行します。WindowsクライアントにログインしてChromeブラウザを開き、DVWAのSQL Injectionページより、User ID に 'or 1=1 # と入力して、SQLインジェクション攻撃を実行します。
今回は、アプリケーションにWAFポリシーが適用されているため、攻撃はrejectされます。
BIG-IP Next WAFが攻撃をブロックしたことを示す、以下のような画面が表示されることを確認します。

   .. image:: images/Picture13.png
      :scale: 60%
      :align: center
   |

