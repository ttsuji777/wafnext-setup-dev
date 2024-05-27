脆弱なウェブサーバーをデプロイ
=========================================================

UDF画面上部タブの"DEPLOYMENT"をクリックし、BIG-IP Next Central Managerインスタンスの"ACCESS" > "GUI" を選択します。

   .. image:: images/Picture01.png
      :scale: 80%
      :align: center
   |

BIG-IP Next Central Manager GUIのログイン画面が表示されたら、以下のユーザー名/パスワードを入力してログインします。

   - ユーザー名/パスワード:
   - **admin/Welcome123!**

   .. image:: images/Picture2.png
      :scale: 90%
      :align: center
   |       

ログインすると、次のようなホーム画面になります。"Manage Applications" > "Go to Application Workspace"をクリックします。

   .. image:: images/Picture3.png
      :scale: 15%
      :align: center
   |       

“Start Adding Apps”をクリックして、新規アプリケーション作成します。

   .. image:: images/Picture4.png
      :scale: 50%
      :align: center
   |       

- Application Service Name:
   - **HTTP-DVWA**　（任意の名前）
- What kind of Application:
   - **Standard**　を選択
- **“Start Creating”** を二回クリック


   .. image:: images/Picture5.png
      :scale: 30%
      :align: center
   |       

“Pools”を選択し、“Create”をクリックしてpoolの名前とポート番号を入力します。

- Pool Name:
   - **dvwa_pool**
- Server Port:
   - **80**
- Load-Balancing Mode:
   - **round-robin**
- Monitor Type:
   - **http**


   .. image:: images/Picture6.png
      :scale: 20%
      :align: center
   |       

"Virtual Servers"のタブに戻り、以下内容を入力します。

- Virtual Server Name:
   - **DVWA-VS**
- Pool:
   - **dvwa_pool**　(先ほど作成されたpoolを選択)
- **“Review & Deploy”** をクリック

   .. image:: images/Picture7.png
      :scale: 20%
      :align: center
   |       

次の画面から"Start Adding"をクリック、“big01.f5lab.local” のチェックボックスをチェックしてから"Add to List"をクリックします。

   .. image:: images/Picture8.png
      :scale: 30%
      :align: center
   |       

次のDeploy画面で、Virtual ServerのIPとPool memberを設定します。

- Virtual Address:
   - **10.1.10.100**
- Membersの下矢印を展開し、 “+Pool Members” をクリック

   .. image:: images/Picture9.png
      :scale: 15%
      :align: center
   |       

“+Add Row” を1回クリックして、pool memberを作成します。

- Name:
   - **dvwa_server**
- IP Address:
   - **10.1.20.101**
- 入力後、 ”Save” をクリック

   .. image:: images/Picture10.png
      :scale: 20%
      :align: center
   |       

設定内容に問題ないかを適用前に"Validate All"で検証し、エラーがなければ"Deploy Changes"をクリックして本番適用します。

   .. image:: images/Picture11.png
      :scale: 20%
      :align: center
   |       

以下の画面で、”Yes, Deploy”をクリックします。

   .. image:: images/Picture12.png
      :scale: 80%
      :align: center
   |       

デプロイ完了後、Dashboardから作成されたアプリケーション"HTTP-DVWA"を確認出来ます。

   .. image:: images/Picture13.png
      :scale: 20%
      :align: center
   |       


UDF画面上部タブの"DEPLOYMENT"をクリックし、”windows10 client”の"ACCESS" > "CONSOLE"もしくは”RDP”を選択します。以下のユーザー名とパスワードで、Windowsクライアントにログインします。

   - ユーザー名/パスワード:
   - **user/user**

   .. note::
      セキュリティ上の理由等でRDP (Remote Desktop Protocol)が利用できない場合は、"CONSOLE"を選択してください。


   .. image:: images/Picture14.png
      :align: center
   |   

Windowsクライアント上でChromeブラウザを開き、http://10.1.10.100/DVWA/login.php にアクセスします。DVWAのログイン画面が表示されたら、ユーザ名/パスワードを入力してログインします。

   - Username/Password:
   - **admin/password**

   .. image:: images/Picture16.png
      :align: center
   |       

”DVWA Security”を選択して、Security Level を Low に設定し、”Submit”をクリックします。


   .. image:: images/Picture17.png
      :align: center
   |       
”SQL Injection”を選択し、User IDに「'or 1=1 #」と入力して、SQLインジェクション攻撃を実行します (本ガイドからコマンドはコピーしないで下さい。シングルクォーテーションに注意してタイプしてください。)。

SQLインジェクション攻撃が成功し、ユーザー情報を取得できることを確認します。


   .. image:: images/Picture15.png
      :align: center
   |   
