# simpleNotificator
A simple jQuery notification plugin

##What is a simpleNotificator?

simpleNotificator is a simple jQuery based plugin, allow create informative notification quickly and easily!

##How to get started?

Installing the plugin is easy as pie! Copy stylesheet (css) and JavaScript (js) files to your folder and add the following HTML code snippet between the <header></header> tags.

<link href="simpleNotificator.css" rel="stylesheet" type="text/css" />
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.0/jquery.min.js"></script>
<script src="simpleNotificator.jQuery.js"></script>

Pay attention: if you are copying the stylesheet & JavaScript to sub directories, make sure you change the paths in the code snippet above.

##How do I use this plugin?

All you need to do is define where the notification should be appended, set the notification message and if you wish, customize the notification and add a custom callback.
In the examples below we will append all notifications to a div element with a "notificationBlock" id attribute.

**Generate An Info Notification**
$('#notificationBlock').notification('This is an info notification', function () {
    // Customized callback function
});

**Generate A Success Notification**
$('#notificationBlock').successNotification('This is a success notification', function () {
    // Customized callback function
});
    
**Generate A Warning Notification**
$('#notificationBlock').warningNotification('This is a warning notification', function () {
    // Customized callback function
});
    
**Generate A Danger Notification**
$('#notificationBlock').dangerNotification('This is a error notification', function () {
    // Customized callback function
});

##How can I customize the notification?

simpleNotificator expects to get up to 3 arguments:
1. Notification message - what will be appeared in the notification body?
2. An options object - allow you to override some default settings of the notification.
3. Callback - A function that will be invoked after the plugin operation is done.

Let's get to the point, in order to customize the notification, you will have to provide the option object in the following format:

$('#notificationBlock').notification('Notification message', {
    position: 'top',
    textPrefix: 'Aloha!',
    stickMode: true,
    width: '50%' 
    },function () {
    // Customized callback function goes here
});

As you can see, above I've provided the second argument - the options object.
The customized notification will be appended at the beginning of the #notificationBlock element, the message prefix will be "Aloha!", the notification will be sticky and the notification width will be 50% out of its parent element.
Easy, isn't?
 
##All the available customizations: 

- inAnimationEffect: Object to define the "entering" animation effect - Default : {opacity: 1}
- inAnimationDuration: Integer to define the "entering" animation duration in ms - Default : 600 
- outAnimationEffect: Object to define the "exiting" animation effect - Default : {opacity: 0}
- outAnimationDuration: Integer to define the "exiting" animation duration in ms - Default : 600
- outDelay: Integer to define the "lifetime" of the notification once its fully created - Default : 2000
- hoverDelay: Integer to define the delay that will be caused in case of mouse hover on the notification - Default : 1000
- position: 'top' for appending to the beginning of the element and 'bottom' to its end - Default : 'bottom'
- textPrefix: Define a text that will be prefixing the notification message - Default : 'Pay attention!'
- stickMode: Choose whether you like the notification to be sticky (true) or not (false) - Default : false
- width: Choose the notification width in pixels, percentages, points, etc - Default :'100%'

##Free to you all!

Feel free to use, adjust, destroy and rebuild for your commercial and own needs.
Keeping my copyrights at the JavaScript code would be highly appreciated.