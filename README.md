omelo-zookeeper-plugin
====================

omelo-zookeeper-plugin is a plugin for omelo, it can be used in omelo(>=1.0-pre).

omelo-zookeeper-plugin provides zookeeper service for the cluster. omelo uses the master server to manage all other servers, and it is very suitable for small and medium size cluster, for it costs little and it is very flexible. As all we know, most large distributed systems use zookeeper to manage servers, so in 1.0(1.0-pre) of omelo we introduce the zookeeper plugin. And this plugin's job is just to notify all other servers that the current alived servers of the cluster when new server added or old server removed. The origin master server is still useful for managing modules and monitoring.

##Installation

```
npm install omelo-zookeeper-plugin
```

##Usage

```
var zookeeper = require('omelo-zookeeper-plugin');

app.configure('production|development', function() {
 
 // close master cluster management
	app.set('masterConfig', {
		closeWatcher: true
	});

// close master cluster management
	app.set('monitorConfig', {
		closeWatcher: true
	});

	app.use(zookeeper, {
		zookeeper: {
			server: '127.0.0.1:2181',
			path: '/omelo/servers',
			username: 'omelo',
			password: 'omelo'
		}
	});
});

```