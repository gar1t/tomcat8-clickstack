# Tomcat 8 ClickStack

To use: 

    bees app:deploy -t tomcat8 -a APP_ID WAR_FILE

Tomcat 8 ClickStack for CloudBees PaaS.


# Build 

    $  gradlew clean installApp distZip

After successful build tomcat8-plugin.zip is created and can be uploaded to the CloudBees platform location by the CloudBees team.

# Local development

Note: You should be familiar with developing ClickStacks using the genapp system first. \[[see docs](http://genapp-docs.cloudbees.com/quickstart.html)\]

* Build the plugin project using make to prepare for use in local app deploys
* In plugins\_home, add a symlink to the tomcat8-clickstack/pkg dir named 'tomcat8'

  $ ln -s tomcat8-clickstack/pkg PLUGINS\_HOME/tomcat8

* In your metadata.json, you can now reference the stack using the name 'tomcat8'

    { "app": {  "plugins": ["tomcat8"] } }


Once the plugin is published to a public URL, you can update an app to use it with the CloudBees SDK:

    $ bees app:deploy -a APP_ID -t tomcat8 -RPLUGIN.SRC.tomcat8=URL_TO_YOUR_PLUGIN_ZIP PATH_TO_WARFILE


## TODOs
- [ ] Add idle/active timeouts
- [ ] Add private app support (perhaps via router instead?)
- [ ] Add cloudbees-web.xml support

