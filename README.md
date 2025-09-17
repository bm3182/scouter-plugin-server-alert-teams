# scouter-plugin-server-alert-teams
### Scouter server plugin to send a alert via teams

- this project inspired by telegram plugin project of noces96. it is very similar.

- this project is  scouter server plugin project. this project goal is that send message to teams.
-  this project only support a sort of Alert.
    - CPU of Agent  (warning / fatal)
    - Memory of Agent (warning / fatal)
    - Disk of Agent (warning / fatal)
    - connected new Agent
    - disconnected Agent
    - reconnect Agent

### Properties (you can modify in conf/scouter.conf of scouter server home )
* **_ext\_plugin\_teams\_send\_alert_** : can send teams message or can'not  (true / false) - default : false
* **_ext\_plugin\_teams\_debug_** : can log message or can't  - default false
* **_ext\_plugin\_teams\_level_** : log level (0 : INFO, 1 : WARN, 2 : ERROR, 3 : FATAL) - default 0
* **_ext\_plugin\_teams\_webhook_url_** : Teams WebHook URL
* **_ext\_plugin\_teams\_channel_** : #Channel or @user_id
* **_ext\_plugin\_elapsed\_time\_threshold_** : Response time threshold (ms) - Default 0 , 0 means that the response time threshold is not checked.
* **_ext\_plugin\_gc\_time\_threshold_** : Threshold for GC Time (ms) - Default 0, 0 means that GC Time is not checked for exceeding the threshold.
* **_ext\_plugin\_thread\_count\_threshold_** : Threshold for Thread Count - Default 0, 0 means that Thread Count threshold is not checked.
* **_ext\_plugin\_teams\_xlog\_enabled_** : xlog message send (true / false) - default : false
* **_ext_plugin_teams_object_alert_enabled_** : object active/dead alert (true / false) - default : false
* **_ext_plugin_ignore_duplicate_alert_** : ignore duplicate notifications or not (true / false) - default : false


* Example
```
# Heap Used의 임계치 (M) - 기본 값은 0으로, 0일때 Heap Used의 임계치 초과 여부를 확인하지 않는다.
ext_plugin_heap_used_threshold=2000
ext_plugin_4G_heap_used_threshold=4000
ext_plugin_6G_heap_used_threshold=6000
ext_plugin_8G_heap_used_threshold=7800
# Heap Used의 임계치 적용 대상 서버
ext_plugin_heap_8g_servers=/gprtwas1/wise_prd11,/gprtwas1/wise_prd12,/gprtwas2/wise_prd21,/gprtwas2/wise_prd22
ext_plugin_heap_6g_servers=/pEacA1/PFLS_LIVE1,/pEacA2/PFLS_LIVE2,/cjwas03/qmswas1,/cjwas04/qmswas2
ext_plugin_heap_4g_servers=/cjwas03/expwas01,/cjwas04/expwas02,/cjwas03/amsprd_1,/cjwas04/amsprd_2,/cjwas03/cmsprd_1,/cjwas04/cmsprd_2,/cjirisap1/bmis_was1,/cjirisap1/iris_was1,/cjemap/bmis_was2,/cjemap/iris_was2

# External Interface (Teams)
# Teams 메시지 발송 여부 (true / false) - 기본 값은 false
ext_plugin_teams_send_alert=true
# xlog system alert - 기본 값은 false
ext_plugin_wise_teams_xlog_enabled=false
ext_plugin_esc_teams_xlog_enabled=true
ext_plugin_exp_teams_xlog_enabled=true
ext_plugin_igap_teams_xlog_enabled=true
ext_plugin_tms_teams_xlog_enabled=true
ext_plugin_mpro_teams_xlog_enabled=true
ext_plugin_cis_teams_xlog_enabled=true
ext_plugin_ods_teams_xlog_enabled=true
ext_plugin_cpl_teams_xlog_enabled=true
ext_plugin_qms_teams_xlog_enabled=true
ext_plugin_bmis_teams_xlog_enabled=true
ext_plugin_iris_teams_xlog_enabled=true
ext_plugin_pfls_teams_xlog_enabled=true
ext_plugin_meta_teams_xlog_enabled=true
ext_plugin_ams_teams_xlog_enabled=true
ext_plugin_cms_teams_xlog_enabled=true
ext_plugin_fta_teams_xlog_enabled=true
ext_plugin_hanaro_teams_xlog_enabled=true
ext_plugin_wings_teams_xlog_enabled=true
# 로깅 여부 - 기본 값은 false
ext_plugin_teams_debug=true
# 수신 레벨(0 : INFO, 1 : WARN, 2 : ERROR, 3 : FATAL) - 기본 값은 0
ext_plugin_teams_level=2
# Teams WebHook : https://cjworld.webhook.office.com/webhookb2/547d96eb-3d0e-4d56-aa8f-8164946e6a93@ee6af5c5-684f-4539-9eb6-64793af08027/IncomingWebhook/fdf6b83ecd54438491f239973eef897d/7424369a-02ba-469f-8a14-5c90eb8766b8
# Teams WebHook2 : https://cjworld.webhook.office.com/webhookb2/547d96eb-3d0e-4d56-aa8f-8164946e6a93@ee6af5c5-684f-4539-9eb6-64793af08027/IncomingWebhook/fdf6b83ecd54438491f239973eef897d/7424369a-02ba-469f-8a14-5c90eb8766b8/V26bTkcvGcMdsH5GvmyZi8yFPBpMe3LNv3m9hiJCYX2Ik1
ext_plugin_teams_webhook_url=https://cjworld.webhook.office.com/webhookb2/547d96eb-3d0e-4d56-aa8f-8164946e6a93@ee6af5c5-684f-4539-9eb6-64793af08027/IncomingWebhook/fdf6b83ecd54438491f239973eef897d/7424369a-02ba-469f-8a14-5c90eb8766b8/V26bTkcvGcMdsH5GvmyZi8yFPBpMe3LNv3m9hiJCYX2Ik1
# Teams Channel
ext_plugin_teams_channel=General
# 설정에 쉼표로 UPN을 넣으면(예: alice@contoso.com,bob@contoso.com)
ext_plugin_teams_mention_users=
# UPN 대신 별칭(닉네임)
ext_plugin_teams_mention_use_alias=true
# 분기 규칙 선언(쉼표 구분, 앞에서부터 우선 적용)
ext_plugin_teams_rules=mpro,exp,tms,ods,ams,hanaro,cjwings,fta,qms,cis,igap,esc,cpl,wise,iris,cms,pfls,meta,defaultOncall
ext_plugin_teams_rule.mpro.when.contains=mproWas
ext_plugin_teams_rule.mpro.mentions=hyeonmoyu@cj.net|유현모님,lifeoffree@cj.net|이규호님,kwanggin@cj.net|이광진님
ext_plugin_teams_rule.exp.when.contains=expwas
ext_plugin_teams_rule.exp.mentions=kwanggin@cj.net|이광진님,sugong@cj.net|박수경님,roe961@cj.net|이영훈님
ext_plugin_teams_rule.tms.when.contains=tmsprd
ext_plugin_teams_rule.tms.mentions=kwanggin@cj.net|이광진님,sleej0102@cj.net|이종수님, 김순화님, sugong@cj.net|박수경님,roe961@cj.net|이영훈님
ext_plugin_teams_rule.ods.when.contains=odsprd
ext_plugin_teams_rule.ods.mentions=kwanggin@cj.net|이광진님,jaekyung@cj.net|이재경님, sugong@cj.net|박수경님,roe961@cj.net|이영훈님
ext_plugin_teams_rule.ams.when.contains=amsprd
ext_plugin_teams_rule.ams.mentions=kwanggin@cj.net|이광진님,sugong@cj.net|박수경님,jaekyung@cj.net|이재경님,roe961@cj.net|이영훈님
ext_plugin_teams_rule.hanaro.when.contains=HANARO
ext_plugin_teams_rule.hanaro.mentions=kwanggin@cj.net|이광진님,soonding@cj.net|김순화님,sleej0102@cj.net|이종수님,sugong@cj.net|박수경님,roe961@cj.net|이영훈님
ext_plugin_teams_rule.cjwings.when.contains=WINGS_PRD
ext_plugin_teams_rule.cjwings.mentions=kwanggin@cj.net|이광진님,soonding@cj.net|김순화님,sleej0102@cj.net|이종수님,sugong@cj.net|박수경님,roe961@cj.net|이영훈님
ext_plugin_teams_rule.fta.when.contains=fta
ext_plugin_teams_rule.fta.mentions=kwanggin@cj.net|이광진님,pji2503@cj.net|박주일님,jhungminji@cj.net|정민지님
ext_plugin_teams_rule.qms.when.contains=qmswas
ext_plugin_teams_rule.qms.mentions=karis6@cj.net|남형주님,etakhee@cj.net|이탁희님,mcshin19@cj.net|신민철님
ext_plugin_teams_rule.cis.when.contains=cis
ext_plugin_teams_rule.cis.mentions=hihaaa@cj.net|신효진님,etakhee@cj.net|이탁희님,
ext_plugin_teams_rule.igap.when.contains=igap_was
ext_plugin_teams_rule.igap.mentions=soom@cj.net|이수미님,seojy@cj.net|서지윤님,bangalo1@cj.net|이상엽님
ext_plugin_teams_rule.esc.when.contains=esc
ext_plugin_teams_rule.esc.mentions=soom@cj.net|이수미님,bangalo1@cj.net|이상엽님,river2745@cj.net|박가람님
ext_plugin_teams_rule.cpl.when.contains=cpl
ext_plugin_teams_rule.cpl.mentions=soom@cj.net|이수미님,seojy@cj.net|서지윤님,bangalo1@cj.net|이상엽님
ext_plugin_teams_rule.wise.when.contains=wise_prd|wise_mprd
ext_plugin_teams_rule.wise.mentions=soom@cj.net|이수미님,msryu52@cj.net|유명선님,svoice@cj.net|서종호님,wschoi9@cj.net|최우석님
ext_plugin_teams_rule.iris.when.contains=iris|bmis
ext_plugin_teams_rule.iris.mentions=soom@cj.net|이수미님,msryu52@cj.net|유명선님,wschoi9@cj.net|최우석님,heesun_@cj.net|윤희선님
ext_plugin_teams_rule.cms.when.contains=cmsprd
ext_plugin_teams_rule.cms.mentions=soom@cj.net|이수미님,seojy@cj.net|서지윤님,bangalo1@cj.net|이상엽님,river2745@cj.net|박가람님,baebully@cj.net|배정관님,angle1339@cj.net|송효주님,yhseung@cj.net|양효승님,nnn0111123@cj.net|김소미님
ext_plugin_teams_rule.pfls.when.contains=PFLS|EGGPLAN
ext_plugin_teams_rule.pfls.mentions=yhm0402@cj.net|윤현민님,yh0219@cj.net|김용현님,hoyoung0713@cj.net|채호영님,heesun_@cj.net|윤희선님,msryu52@cj.net|유명선님,yjs301@cj.net|유재승님
ext_plugin_teams_rule.meta.when.contains=cj-meta-app
ext_plugin_teams_rule.meta.mentions=yjs301@cj.net|유재승님
# 어떤 규칙도 안 맞으면 → 온콜 1명 멘션
ext_plugin_teams_rule.defaultOncall.when.contains=*
ext_plugin_teams_rule.defaultOncall.mentions=bm3182@cj.net|정기수님
# 관리자는 모두 받도록
ext_plugin_teams_global_mentions=bm3182@cj.net|정기수님
# xlog system alert - 기본 값은 false
ext_plugin_teams_xlog_enabled=false
# Object alert - 기본 값은 false
ext_plugin_teams_object_alert_enabled=true
# 연속된 동일 Alert을 1시간 동안 제외 - 기본 값은 false
ext_plugin_ignore_duplicate_alert=true
```

### Dependencies
* Project
    - scouter.common
    - scouter.server
* Library
    - commons-codec-1.9.jar
    - commons-logging-1.2.jar
    - gson-2.6.2.jar
    - httpclient-4.5.2.jar
    - httpcore-4.4.4.jar

### Build & Deploy

* Build
    - Build Artifacts as a jar file
  
    
* Deploy
    - After build, an out directory is created under the project → Copy the scouter-plugin-server-alert-teams.jar created under the out folder and dependency library  →  save it to the lib/ folder under the scouter server installation path.
