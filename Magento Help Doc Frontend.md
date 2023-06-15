# ![](https://th.bing.com/th?id=ODLS.194d04fb-feff-41d9-b83c-1cbe98afa6ec&w=32&h=32&o=6&pid=13.1) **<font color=""> Magento Training Exercises</font>**
>### **<font color="#4267b2"> Chapter # 1 Exercises</font>**

#### Exercises # 1.1
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
<details><summary markdown="span">Picture of module <code>HelloWorld</code></summary>

![](https://raw.githubusercontent.com/R-jee/Magento2-Helping-Guide/87a64196d84f3a2ce305d956b74b7e09a5973a52/Screenshot%20from%202023-06-09%2011-49-09.png)
</details>

***

#### Exercises # 1.2
###### **<font color="Green">Answer</font>**
1.2.1. Browse the Magento codebase & list all possible config files in the <Module>/etc folder.

- <small>To list all the possible config files in `<Module>/etc` folder </small>
```shell
find vendor/magento/ -type f -name '*.xml' | grep -v '/Test/' | grep -v '/dev/' | sed -n 's/.*etc\///p' | sort -n | uniq
```
<details><summary markdown="span"><font color="#f5deb3">See all possible config files</font></summary>

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
<details><summary markdown="span"><font color="#f5deb3">See possible areas</font></summary>

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

#### Exercises # 1.3
###### **<font color="Green">Answer</font>**
1.3.1. Create a Preference for `Magento\Theme\Block\Html\Footer`. Modify the method `getCopyright()` so that it adds the text `"Hello World"` next to copyright.
- <small>First created a module `Unit1/AfterFooter` create etc/module.xml & registration.php file </small>
- <small>Create depandency config file `etc/frontend/di.xml` </small>
- <small>Create `<module>/Block/Html/Footer.php` file to modify `getCopyright()` function</small>
<details><summary markdown="span"><font color="#f5deb3">Picture of module <code>AfterFooter</code> & enabled it.</font></summary>

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
<details><summary markdown="span"><font color="#f5deb3">Picture of module disabled <code>AfterFooter</code></font></summary>

![](https://github.com/R-jee/Magento2-Helping-Guide/blob/main/Screenshot%20from%202023-06-12%2013-43-02.png?raw=true)
</details>

***

#### Exercises # 1.4
###### **<font color="Green">Answer</font>**
1.4.1. Create an After plugin to the `\Magento\Framework\App\Action\Action::dispatch` method which is called every time magento processes a URL. Make this plugin only work on frontend.
- <small>Created After-plugin type `Unit1AfterPluginAction` to get the URL request action name as result from Magento action dispatch method</small>
- <small>Created DI in `etc/frontend/di.xml` folder to Make this plugin only work on frontend</small>

1.4.2. Inject `Psr\Log\LoggerInterface` into plugin's constructor.
- <small>Use LoggerInterface to log the output for URL request action name</small>

1.4.3. Access an instance of action class in the plugin & call `$subject->getRequest()->getFullActionName()` to get full action name that corresponds to the URL.
- <small>Use the `$subject->getRequest()->getFullActionName()` to get the URL action request Full-name</small>

1.4.4. Log this info using `LoggerInterface`.
<details><summary markdown="span"><font color="#f5deb3">Log output image</font></summary>

![](https://github.com/R-jee/Magento2-Helping-Guide/blob/main/Screenshot%20from%202023-06-12%2018-36-43.png?raw=true)
</details>

1.4.5. Find the file it logs to & find your record.
- <small>Log output file location `var/log/system.log` </small>

***

#### Exercises # 1.5
###### **<font color="Green">Answer</font>**
- <small>Created Action Observer `Unit1ActionObserver` to get the URL request action name as result from Magento action dispatch method</small>
- <small>Created `etc/frontend/events.xml` to config this observer only work on frontend</small>
- <small>Use LoggerInterface to log the output for URL request action name</small>
- <small>Use the `$this->request->getFullActionName()` to get the URL action request Full-name</small>
- <small>Log output file location `var/log/system.log` </small>
<details><summary markdown="span"><font color="#f5deb3">Log output image</font></summary>

![](https://github.com/R-jee/Magento2-Helping-Guide/blob/main/Screenshot%20from%202023-06-13%2014-07-47.png?raw=true)
</details>

***

#### Exercises # 1.6
###### **<font color="Green">Answer</font>**
1.6.1. <small>Get list of all magento available commands </small>
```shell
php bin/magento
```
<details><summary markdown="span"><font color="#f5deb3">Show all Magento available commands </font></summary>

**Magento CLI 2.4.6**
```
Usage:
  command [options] [arguments]

Options:
  -h, --help            Display help for the given command. When no command is given display help for the list command
  -q, --quiet           Do not output any message
  -V, --version         Display this application version
      --ansi|--no-ansi  Force (or disable --no-ansi) ANSI output
  -n, --no-interaction  Do not ask any interactive question
  -v|vv|vvv, --verbose  Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug

Available commands:
  completion                                           Dump the shell completion script
  help                                                 Display help for a command
  list                                                 List commands
 admin
  admin:adobe-ims:disable                              Disable Adobe IMS Module
  admin:adobe-ims:enable                               Enable Adobe IMS Module.
  admin:adobe-ims:info                                 Information of Adobe IMS Module configuration
  admin:adobe-ims:status                               Status of Adobe IMS Module
  admin:user:create                                    Creates an administrator
  admin:user:unlock                                    Unlock Admin Account
 app
  app:config:dump                                      Create dump of application
  app:config:import                                    Import data from shared configuration files to appropriate data storage
  app:config:status                                    Checks if config propagation requires update
 braintree
  braintree:migrate                                    Migrate stored cards from a Magento 1 database
 cache
  cache:clean                                          Cleans cache type(s)
  cache:disable                                        Disables cache type(s)
  cache:enable                                         Enables cache type(s)
  cache:flush                                          Flushes cache storage used by cache type(s)
  cache:status                                         Checks cache status
 catalog
  catalog:images:resize                                Creates resized product images
  catalog:product:attributes:cleanup                   Removes unused product attributes.
 cms
  cms:wysiwyg:restrict                                 Set whether to enforce user HTML content validation or show a warning instead
 config
  config:sensitive:set                                 Set sensitive configuration values
  config:set                                           Change system configuration
  config:show                                          Shows configuration value for given path. If path is not specified, all saved values will be shown
 cron
  cron:install                                         Generates and installs crontab for current user
  cron:remove                                          Removes tasks from crontab
  cron:run                                             Runs jobs by schedule
 customer
  customer:hash:upgrade                                Upgrade customer's hash according to the latest algorithm
 deploy
  deploy:mode:set                                      Set application mode.
  deploy:mode:show                                     Displays current application mode.
 dev
  dev:di:info                                          Provides information on Dependency Injection configuration for the Command.
  dev:email:newsletter-compatibility-check             Scans newsletter templates for potential variable usage compatibility issues
  dev:email:override-compatibility-check               Scans email template overrides for potential variable usage compatibility issues
  dev:profiler:disable                                 Disable the profiler.
  dev:profiler:enable                                  Enable the profiler.
  dev:query-log:disable                                Disable DB query logging
  dev:query-log:enable                                 Enable DB query logging
  dev:source-theme:deploy                              Collects and publishes source files for theme.
  dev:template-hints:disable                           Disable frontend template hints. A cache flush might be required.
  dev:template-hints:enable                            Enable frontend template hints. A cache flush might be required.
  dev:template-hints:status                            Show frontend template hints status.
  dev:tests:run                                        Runs tests
  dev:urn-catalog:generate                             Generates the catalog of URNs to *.xsd mappings for the IDE to highlight xml.
  dev:xml:convert                                      Converts XML file using XSL style sheets
 downloadable
  downloadable:domains:add                             Add domains to the downloadable domains whitelist
  downloadable:domains:remove                          Remove domains from the downloadable domains whitelist
  downloadable:domains:show                            Display downloadable domains whitelist
 encryption
  encryption:payment-data:update                       Re-encrypts encrypted credit card data with latest encryption cipher.
 events
  events:create-event-provider                         [events:provider:create ] Create a custom event provider in Adobe I/O Events for this instance. If you do not specify the label and description options, they must be defined in the system app/etc/event-types.json file.
  events:generate:module                               Generate module based on plugins list
  events:info                                          Returns the payload of the specified event.
  events:list                                          Shows list of subscribed events
  events:list:all                                      Returns a list of subscribable events defined in the specified module
  events:metadata:populate                             Creates metadata in Adobe I/O from the configuration list (XML and application configurations)
  events:subscribe                                     Subscribes to the event
  events:sync-events-metadata                          Synchronise event metadata for this instance
  events:unsubscribe                                   Removes the subscription to the supplied event
 i18n
  i18n:collect-phrases                                 Discovers phrases in the codebase
  i18n:pack                                            Saves language package
  i18n:uninstall                                       Uninstalls language packages
 indexer
  indexer:info                                         Shows allowed Indexers
  indexer:reindex                                      Reindexes Data
  indexer:reset                                        Resets indexer status to invalid
  indexer:set-dimensions-mode                          Set Indexer Dimensions Mode
  indexer:set-mode                                     Sets index mode type
  indexer:show-dimensions-mode                         Shows Indexer Dimension Mode
  indexer:show-mode                                    Shows Index Mode
  indexer:status                                       Shows status of Indexer
 info
  info:adminuri                                        Displays the Magento Admin URI
  info:backups:list                                    Prints list of available backup files
  info:currency:list                                   Displays the list of available currencies
  info:dependencies:show-framework                     Shows number of dependencies on Magento framework
  info:dependencies:show-modules                       Shows number of dependencies between modules
  info:dependencies:show-modules-circular              Shows number of circular dependencies between modules
  info:language:list                                   Displays the list of available language locales
  info:timezone:list                                   Displays the list of available timezones
 inventory
  inventory:reservation:create-compensations           Create reservations by provided compensation arguments
  inventory:reservation:list-inconsistencies           Show all orders and products with salable quantity inconsistencies
 inventory-geonames
  inventory-geonames:import                            Download and import geo names for source selection algorithm
 maintenance
  maintenance:allow-ips                                Sets maintenance mode exempt IPs
  maintenance:disable                                  Disables maintenance mode
  maintenance:enable                                   Enables maintenance mode
  maintenance:status                                   Displays maintenance mode status
 media-content
  media-content:sync                                   Synchronize content with assets
 media-gallery
  media-gallery:sync                                   Synchronize media storage and media assets in the database
 module
  module:config:status                                 Checks the modules configuration in the 'app/etc/config.php' file and reports if they are up to date or not
  module:disable                                       Disables specified modules
  module:enable                                        Enables specified modules
  module:status                                        Displays status of modules
  module:uninstall                                     Uninstalls modules installed by composer
 newrelic
  newrelic:create:deploy-marker                        Check the deploy queue for entries and create an appropriate deploy marker.
 queue
  queue:consumers:list                                 List of MessageQueue consumers
  queue:consumers:restart                              Restart MessageQueue consumers
  queue:consumers:start                                Start MessageQueue consumer
 remote-storage
  remote-storage:sync                                  Synchronize media files with remote storage.
 sampledata
  sampledata:deploy                                    Deploy sample data modules for composer-based Magento installations
  sampledata:remove                                    Remove all sample data packages from composer.json
  sampledata:reset                                     Reset all sample data modules for re-installation
 security
  security:recaptcha:disable-for-user-forgot-password  Disable reCAPTCHA for admin user forgot password form
  security:recaptcha:disable-for-user-login            Disable reCAPTCHA for admin user login form
 setup
  setup:backup                                         Takes backup of Magento Application code base, media and database
  setup:config:set                                     Creates or modifies the deployment configuration
  setup:db-data:upgrade                                Installs and upgrades data in the DB
  setup:db-declaration:generate-patch                  Generate patch and put it in specific folder.
  setup:db-declaration:generate-whitelist              Generate whitelist of tables and columns that are allowed to be edited by declaration installer
  setup:db-schema:add-slave                            Move checkout quote related tables to a separate DB server
  setup:db-schema:split-quote                          Move checkout quote related tables to a separate DB server. Deprecated since 2.4.2 and will be removed
  setup:db-schema:split-sales                          Move sales related tables to a separate DB server. Deprecated since 2.4.2 and will be removed
  setup:db-schema:upgrade                              Installs and upgrades the DB schema
  setup:db:status                                      Checks if DB schema or data requires upgrade
  setup:di:compile                                     Generates DI configuration and all missing classes that can be auto-generated
  setup:install                                        Installs the Magento application
  setup:performance:generate-fixtures                  Generates fixtures
  setup:rollback                                       Rolls back Magento Application codebase, media and database
  setup:static-content:deploy                          Deploys static view files
  setup:store-config:set                               Installs the store configuration. Deprecated since 2.2.0. Use config:set instead
  setup:uninstall                                      Uninstalls the Magento application
  setup:upgrade                                        Upgrades the Magento application, DB data, and schema
 store
  store:list                                           Displays the list of stores
  store:website:list                                   Displays the list of websites
 support
  support:backup:code                                  Create Code backup
  support:backup:db                                    Create DB backup
  support:utility:check                                Check required backup utilities
  support:utility:paths                                Create utilities paths list
 theme
  theme:uninstall                                      Uninstalls theme
 varnish
  varnish:vcl:generate                                 Generates Varnish VCL and echos it to the command line
```
</details>

1.6.2. <small>Get list of all magento Active & Inactive modules </small>
```shell
php bin/magento module:status
```

1.6.3. <small>Clean the cache</small>
```shell
php bin/magento cache:clean
```

1.6.4. <small>Clean only config cache</small>
```shell
php bin/magento cache:clean config
```

1.6.5. <small>List of available indexers</small>
<details><summary markdown="span"><font color="#f5deb3">Show available indexers</font></summary>

```
design_config_grid                       Design Config Grid
customer_grid                            Customer Grid
catalog_category_product                 Category Products
catalog_product_category                 Product Categories
catalogrule_rule                         Catalog Rule Product
catalog_product_attribute                Product EAV
inventory                                Inventory
catalogrule_product                      Catalog Product Rule
cataloginventory_stock                   Stock
catalogpermissions_product               Catalog Product Permissions
targetrule_product_rule                  Product/Target Rule
targetrule_rule_product                  Target Rule/Product
catalogpermissions_category              Catalog Category Permissions
catalog_product_price                    Product Price
catalogsearch_fulltext                   Catalog Search
salesrule_rule                           Sales Rule
```
###### **Available Indexer commands**
```
php bin/magento indexer:info     
php bin/magento indexer:reindex  
php bin/magento indexer:reset    
php bin/magento indexer:set-dimensions-mode    
php bin/magento indexer:set-mode
php bin/magento indexer:show-dimensions-mode   
php bin/magento indexer:show-mode
php bin/magento indexer:status
```
</details>

1.6.6. <small>Reindex Price</small>
```shell
php bin/magento indexer:reindex catalog_product_price
```

************************************************************************************************************************************************************************************************************************************************

#### Exercises # 2.1
###### **<font color="Green">Answer</font>**
- <small>Created a module, create preference to modify the class `\Magento\Framework\App\FrontController` </small>
- <small>Use `LoggerInterface` to log info</small>
- <small>In `dispatch` function get list of routes & map these routers class names using `get_class($router)` function</small>

<details><summary markdown="span"><font color="#f5deb3">Show List of Routers log <code>var/log/system.log</code> file</font></summary>

![](https://github.com/R-jee/Magento2-Helping-Guide/blob/main/Screenshot%20from%202023-06-14%2011-49-25.png?raw=true)
</details>

****

#### Exercises # 2.2
###### **<font color="Green">Answer</font>**
- <small>Route of shopping cart page is `/checkout/cart/` </small>
- <small>Action class for shopping cart page is `magento/module-checkout/Controller/Cart/index.php` </small>
```shell
find vendor/magento/module-checkout -name Index.php
```
****

#### Exercises # 2.3
###### **<font color="Green">Answer</font>**
2.3.1. <small>Create Action class for showing empty page</small>
- <small>Create `routes.xml` file that pointed our module</small>
- <small>Created action controller `PageResults.php` with URL-Path `resultobjects/page/pageresults` FrontName - `resultobjects` ID - `resultobjects`</small>
- <small>Checked the output empty page at URL - `/resultobjects/page/pageresults`</small>

<details><summary markdown="span"><font color="#f5deb3"><small>See <code>resultobjects/page/pageresults</code> Output </small></font></summary>

![](https://github.com/R-jee/Magento2-Helping-Guide/blob/main/Screenshot%20from%202023-06-15%2012-02-56.png?raw=true)
</details>

2.3.2. <small>Create Action class for showing Raw Result (return "Hello World")</small>
- <small>Created action controller `RawResults.php` with URL-Path `resultobjects/raw/rawresults` FrontName - `resultobjects` ID - `resultobjects`</small>
- <small>Checked the output Raw Result at URL - `/resultobjects/raw/rawresults`</small>

<details><summary markdown="span"><font color="#f5deb3"><small>See <code>resultobjects/raw/rawresults</code> Output </small></font></summary>

![](https://github.com/R-jee/Magento2-Helping-Guide/blob/main/Screenshot%20from%202023-06-15%2012-11-05.png?raw=true)
</details>

2.3.3. <small>Create Action class for showing Json Result (return array containing "Hello World")</small>
- <small>Created action controller `RawResults.php` with URL-Path `resultobjects/raw/rawresults` FrontName - `resultobjects` ID - `resultobjects`</small>
- <small>Checked the output Raw Result at URL - `/resultobjects/raw/rawresults`</small>

<details><summary markdown="span"><font color="#f5deb3"><small>See <code>resultobjects/raw/rawresults</code> Output </small></font></summary>

![](https://github.com/R-jee/Magento2-Helping-Guide/blob/main/Screenshot%20from%202023-06-15%2012-11-05.png?raw=true)
</details>

