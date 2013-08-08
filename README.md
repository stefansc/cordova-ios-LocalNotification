Cordova Local Notification Plugin
=================================

- Forked from Cordova 2.3.0+ plugin to create local notifications on iOs by Olivier Lesnicki
- adding changes to reduce manual steps and make [plugman](https://github.com/apache/cordova-plugman) compatible from bruchu
- adding foreground and background inspired by drewdahlman

Installing the plugin
---------------------

This is what I do to install:

    $ plugman  --platform ios --project ./platforms/ios --plugin https://github.com/stefansc/cordova-ios-LocalNotification.git

Using the plugin
----------------

	// Schedules a local notification to be triggered after 5 seconds

    window.addNotification({
		fireDate        : Math.round(new Date().getTime()/1000 + 5),
		alertBody       : "This is a local notification.",
		repeatInterval  : "daily",
		soundName       : "beep.caf",
		badge           : 0,
		notificationId  : 123,
		foreground        : function(notificationId){ 
			alert("Hello World! This alert was triggered by notification" + notificationId); 
		}, 
		background        : function(notificationId){ 
			alert("Hello World! This alert was triggered by notification" + notificationId); 
		}  		
	});


To Do
-----
- Implement badges (currently property is ignored)
- JavaScript validation
- support for UILocalNotification.alertAction
