# ![](https://th.bing.com/th?id=ODLS.194d04fb-feff-41d9-b83c-1cbe98afa6ec&w=32&h=32&o=6&pid=13.1) **<font color=""> Magento Training Exercises</font>**

>### **<font color="#4267b2"> Chapter # 1 Exercises</font>**

##### Exercises # 1.1<font color="Yellow"> ( Created an empty Hello World module in app/code & enable it) </font>

###### **<font color="Green">Answer</font>** In this exercise, created an empty module `HelloWorld` and anable it & use these commands

- <small>Enable `Unit1_HelloWorld` module</small>
```shell
sudo php bin/magento module:enable Unit1_HelloWorld
```
- <small>Setup Upgrade</small>
```shell
sudo php bin/magento setup:upgrade
```
- <small>Give Permissions</small>
```shell
sudo chmod -R 777 var/ pub/ generated/ app/etc/
```
<details>
    <summary markdown="span"><font color="#f5deb3">Picture of module <code>HelloWorld</code></font></summary>
    <image src="https://data.terabox.com/thumbnail/80e172adf7d62550bdcb0e975459f4f0?fid=4400792537950-250528-1036449040183911&time=1686308400&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-PImMV6aIFhD%2FCet4Nejd%2BYOytj8%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=247314799587999843&dp-callid=0&size=c1600_u1600&quality=100&vuk=-&ft=video"></image>
</details>

***

##### Exercises # 1.2<font color="Yellow"> ( Browse the Magento codebase & list all possible config files in the <Module>/etc folder. How many areas are used for those files? ) </font>
###### **<font color="Green">Answer</font>**
1.2.1. Browse the Magento codebase & list all possible config files in the <Module>/etc folder.

- <small>To list all the possible config files in `<Module>/etc` folder </small>
```shell
find vendor/magento/ -type f -name '*.xml' | grep -v '/Test/' | grep -v '/dev/' | sed -n 's/.*etc\///p' | sort -n | uniq
```
<details>
<summary markdown="span"><font color="#f5deb3">See all possible config files</font></summary>

```
acl.xml
address_formats.xml
adminhtml/admingws.xml
adminhtml/csp_whitelist.xml
adminhtml/di.xml
adminhtml/events.xml
adminhtml/menu.xml
adminhtml/routes.xml
adminhtml/rules/payment_au.xml
adminhtml/rules/payment_ca.xml
adminhtml/rules/payment_de.xml
adminhtml/rules/payment_es.xml
adminhtml/rules/payment_fr.xml
adminhtml/rules/payment_gb.xml
adminhtml/rules/payment_hk.xml
adminhtml/rules/payment_it.xml
adminhtml/rules/payment_jp.xml
adminhtml/rules/payment_nz.xml
adminhtml/rules/payment_other.xml
adminhtml/rules/payment_us.xml
adminhtml/system/express_checkout.xml
adminhtml/system/payflow_advanced.xml
adminhtml/system/payflow_link.xml
adminhtml/system/payments_pro_hosted_solution_with_express_checkout.xml
adminhtml/system/payments_pro_hosted_solution.xml
adminhtml/system/paypal_payflowpro_with_express_checkout.xml
adminhtml/system/paypal_payflowpro.xml
adminhtml/system.xml
analytics.xml
cache.xml
catalog_attributes.xml
communication.xml
company_acl.xml
config.xml
constraints.xml
countries.xml
cron_groups.xml
crontab/di.xml
crontab/events.xml
crontab.xml
csp_whitelist.xml
data_source/website.xml
db_schema.xml
definition.map.xml
definition.xml
directory.xml
di.xml
eav_attributes.xml
email_templates.xml
esconfig.xml
events.xml
export.xml
extension_attributes.xml
fieldset.xml
frontend/di.xml
frontend/events.xml
frontend/page_types.xml
frontend/routes.xml
frontend/sections.xml
giftregistry.xml
graphql/di.xml
graphql/events.xml
import.xml
indexer.xml
logging.xml
media_content.xml
menu_hierarchy.xml
module.xml
mview.xml
payment.xml
pdf.xml
persistent.xml
product_options.xml
product_types.xml
queue_consumer.xml
queue_publisher.xml
queue_topology.xml
queue.xml
reports.xml
report.xml
resources.xml
sales.xml
search_engine.xml
search_request.xml
validation.xml
view.xml
webapi_async.xml
webapi_rest/di.xml
webapi_rest/events.xml
webapi_soap/di.xml
webapi_soap/events.xml
webapi.xml
webrestrictions.xml
widget.xml
zip_codes.xml

```
</details>

1.2.2. How many areas are used for those files?
- <small>To list all the possible config files in `<Module>/etc` folder </small>
<details>
<summary markdown="span"><font color="#f5deb3">See possible areas</font></summary>

```
/adminhtml
/crontab
/data_source
/frontend
/graphql
/webapi_rest
/ebapi_soap 
```
</details>
