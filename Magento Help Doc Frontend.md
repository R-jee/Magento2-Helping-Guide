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
    <summary markdown="span">Picture of module <code>HelloWorld</code></summary>

![](https://raw.githubusercontent.com/R-jee/Magento2-Helping-Guide/87a64196d84f3a2ce305d956b74b7e09a5973a52/Screenshot%20from%202023-06-09%2011-49-09.png)
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
/webapi_soap 
```
</details>

***

##### Exercises # 1.3<font color="Yellow"> ( Create a Preference for Magento\Theme\Block\Html\Footer. Modify the method getCopyright() so that it adds the text "Hello World" next to copyright ? Disable your customization after verify that it works? ) </font>
###### **<font color="Green">Answer</font>**
1.3.1. Create a Preference for `Magento\Theme\Block\Html\Footer`. Modify the method `getCopyright()` so that it adds the text `"Hello World"` next to copyright.
- <small>First created a module `Unit1/AfterFooter` create etc/module.xml & registration.php file </small>
- <small>Create depandency config file `etc/frontend/di.xml` </small>
- <small>Create `<module>/Block/Html/Footer.php` file to modify `getCopyright()` function</small>
<details>
    <summary markdown="span">Picture of module <code>AfterFooter</code> & enabled it.</summary>

![](https://github.com/R-jee/Magento2-Helping-Guide/blob/main/Screenshot%20from%202023-06-12%2013-24-15.png?raw=true)

![](https://github.com/R-jee/Magento2-Helping-Guide/blob/main/Screenshot%20from%202023-06-12%2013-30-05.png?raw=true)
</details>

1.3.2. Disable your customization after verify that it works?
- <small>Disable the module `Unit1_AfterFooter`</small>
```shell
sudo php bin/magento module:disable Unit1_AfterFooter
```
- <small>Check module status</small>
```shell
php bin/magento module:status Unit1_AfterFooter
```
<details>
    <summary markdown="span">Picture of module disabled <code>AfterFooter</code> & enabled it.</summary>

![](https://github.com/R-jee/Magento2-Helping-Guide/blob/main/Screenshot%20from%202023-06-12%2013-43-02.png?raw=true)
</details>

***

##### Exercises # 1.4<font color="Yellow"> ( Create an After plugin to the \Magento\Framework\App\Action\Action::dispatch method which is called every time magento processes a URL. Make this plugin only work on frontend. -Inject Psr\Log\LoggerInterface into plugin's constructor. Access an instance of action class in the plugin & call $subject->getRequest()->getFullActionName() to get full action name that corresponds to the URL. -Log this info using LoggerInterface. -Find the file it logs to & find your record. ) </font>
###### **<font color="Green">Answer</font>**
1.4.1. Create an After plugin to the `\Magento\Framework\App\Action\Action::dispatch` method which is called every time magento processes a URL. Make this plugin only work on frontend.
- <small>Created After-plugin type `Unit1AfterPluginAction` to get the URL request action name as result from Magento action dispatch method</small>
- <small>Created DI in `etc/frontend/di.xml` folder to Make this plugin only work on frontend</small>

1.4.2. Inject `Psr\Log\LoggerInterface` into plugin's constructor.
- <small>Use LoggerInterface to log the output for URL request action name</small>

1.4.2. Access an instance of action class in the plugin & call `$subject->getRequest()->getFullActionName()` to get full action name that corresponds to the URL.
- <small>Use the `$subject->getRequest()->getFullActionName()` to get the URL action request Full-name</small>
- 
1.4.2. Log this info using `LoggerInterface`.
- <small>Disable the module `Unit1_AfterFooter`</small>
- 
1.4.2. Find the file it logs to & find your record.
- <small>Disable the module `Unit1_AfterFooter`</small>
- https://github.com/R-jee/Magento2-Helping-Guide/blob/main/Screenshot%20from%202023-06-12%2018-36-43.png?raw=true
