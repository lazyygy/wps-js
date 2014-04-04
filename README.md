# wps-js

Standalone JavaScript WPS client.

## Development

### Tomcat configuration

#### Catalina context
A simple configuration of a Tomcat servlet container to develop wps-js is to point the context of the webapp to the Maven target directory. Put the following lines into a file ``<Tomcat dir>\conf\Catalina\localhost\wps-js.xml`` and restart the servlet container:

```
<Context 
  docBase="/your/path/to/wps-js/target/wps-js-1.0.0-SNAPSHOT/" 
/>
```

You can then update the deployed copy by running ``mvn package -DskiptTests=true``.

#### Eclipse WTP

Alternatively configuration with the web tools plug-in in Eclipse: Open your server configuration, then the tab "Modules" and add the path ``<your path>/wps-js/target/wps-js-1.0.0-SNAPSHOT`` as the document base and any path, for example ``/wps-js``.

### Proxy

wps-js needs a proxy server to connect to WPS server instances. A simple one is jproxy, see https://github.com/matthesrieke/jprox. wps-js will by default look for a proxy at ``/wps_proxy/wps_proxy?``.

#### jprox configuration

Make sure you use the following parameters in jprox's ``web.xml`` and deploy it as ``wps_proxy.war`` to make it work with the default wps-js configuration.

```
[...]
<param-name>parameterKey</param-name>
<param-value>url</param-value>
[...]
<servlet-mapping>
	<servlet-name>JProxViaParameterServlet</servlet-name>
	<url-pattern>/</url-pattern>
[...]
```

Alternatively, you can also import jproxy as a project in Eclipse and configure it as a web module for your testing server in the WTP plug-in using the path ``/wps_proxy``.

## License

wps-js is published under Apache Software License, Version 2.0

The used libraries are:

* jQuery - MIT License (https://jquery.org/license/)
* OpenLayers - 2-clause BSD License (http://openlayers.org/)
* js-test-driver - Apache License 2.0 (http://code.google.com/p/js-test-driver/)
