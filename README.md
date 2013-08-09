Cordova Local Notification Plugin
=================================

- Forked from Cordova 2.3.0+ plugin to create local notifications on iOs by Olivier Lesnicki
- adding changes to reduce manual steps and make [plugman](https://github.com/apache/cordova-plugman) compatible by bruchu
- adding foreground and background inspired by drewdahlman

Installing the plugin
---------------------

First you have to take a backup-copy of your cordova_plugins.js because it will be overwrite (i don't know why).

After that you can install the plugin via plugman for example:

    $ plugman install --platform ios --project ./platforms/ios --plugin https://github.com/stefansc/cordova-ios-LocalNotification.git

After that you have to modify your cordova_plugins.js file.


Using the plugin
----------------

	// Schedules a local notification to be triggered after 5 seconds

    localNotification.add({
		fireDate        : Math.round(new Date().getTime()/1000 + 5),
		alertBody       : "This is a local notification.",
		repeatInterval  : "daily",
		soundName       : "horn.caf",
		badge           : 0,
		notificationId  : 123,
		foreground        : function(notificationId){ 
			alert("Hello World! This alert was triggered by notification" + notificationId); 
		}, 
		background        : function(notificationId){ 
			alert("Hello World! This alert was triggered by notification" + notificationId); 
		}  		
	});

	// cancel all local notifications

	localNotification.cancelAll();


To Do
-----
- Implement badges (currently property is ignored)
- JavaScript validation
