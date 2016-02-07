/**
 * SimpleNotificator - jQuery friendly plugin
 *
 * Created by Omer Marcovich on 20/01/2016.
 */

var simpleNotificator = function () {

    var $, settings, notificationSettings, wrapperElement;

    $ = jQuery;

    settings = {
        inAnimationEffect: {opacity: 1},
        inAnimationDuration: 600,
        outAnimationEffect: {opacity: 0},
        outAnimationDuration: 600,
        outDelay: 2000,
        hoverDelay: 1000,
        position: 'bottom',
        type: 'info',
        textPrefix: 'Pay attention!',
        stickMode: false,
        width: '100%',
        callback: null
    };

    // Initializing the containerElement && setting a new wrapperElement
    var initialize = function (containerElement) {

        wrapperElement = $('<div class="notificatorWrapper"></div>');
        setWrapper(wrapperElement);

        return containerElement.append(wrapperElement);
    };

    // Creating a new notification
    var createNotification = function (text, options, callback) {
        // Setting custom settings to each notification element
        notificationSettings = (options) ? $.extend({}, settings, options) : settings;

        // Creating a new notification block
        var newNotification = $('<div style="width:' + notificationSettings.width + '" class="simpleNotification simpleNotification-' + notificationSettings.type + '"><strong>' + notificationSettings.textPrefix + ' </strong>' + text + '</div>');

        // Setting a dismiss button if the notification element is at "stickMode"
        if (notificationSettings.stickMode) {
            $('<button class="dismiss">x</button>').prependTo(newNotification).click(function () {
                notificationSettings.outDelay = 0;
                return dismissNotification(newNotification, notificationSettings);
            });
        }

        //Insert content, specified by the parameter, to the end of each element in the set of matched elements.

        // Appending the new notification element to the end / beelining of the wrapperElement
        switch (notificationSettings.position) {
            case 'bottom':
                wrapperElement.append(newNotification);
                break;
            case 'top':
                wrapperElement.prepend(newNotification);
                break;
            default:
                wrapperElement.append(newNotification);
        }

        return showNotification(newNotification, notificationSettings);
    };

    // Display a notification element on the screen
    var showNotification = function (element, settings) {

        element.animate(settings.inAnimationEffect, settings.inAnimationDuration, function () {
            if (!settings.stickMode) {

                // Set mouseEnter & mouseLeave events for non "sticky" notifications
                element.on('mouseenter', mouseEnterCallback(element));
                element.on('mouseleave', mouseLeaveCallback(element, settings));
            }
        });


        // Call dismiss function if the notification element is not "sticky"
        if (!notificationSettings.stickMode) {
            return dismissNotification(element, settings);
        }
    };

    // Dismiss notification
    var dismissNotification = function (element, settings) {
        element.delay(settings.outDelay).animate(settings.outAnimationEffect, settings.outAnimationDuration, function () {
            // Call to callback function (if exists)
            if (settings.callback) {
                settings.callback.call(this);
            }

            // Remove the notification element
            $(this).remove();
        });
    };

    // Callback for mouseEnter event
    var mouseEnterCallback = function (element) {
        return function () {
            return element.stop(true, true);
        }
    };

    // Callback for mouseLeave event
    var mouseLeaveCallback = function (element, settings) {
        return function () {
            return element.delay(settings.hoverDelay).queue(dismissNotification(element, settings));
        }
    };

    // Set the current wrapperElement
    var setWrapper = function (element) {
        wrapperElement = element;
    };

    return {
        initialize: initialize,
        createNotification: createNotification,
        setWrapper: setWrapper
    };
};

(function ($) {
    var notificator = new simpleNotificator();

    $.fn.notification = function (text, options, callback) {

        if ($(this).find('.notificatorWrapper').length == 0) {
            notificator.initialize($(this));
        } else {
            notificator.setWrapper($(this).children('.notificatorWrapper'));
        }

        if ($.isFunction(options)) {
            callback = options;
            options = {callback: callback};
        } else if ($.isFunction(callback)) {
            options.callback = callback;
        }

        notificator.createNotification(text, options);

        return this;
    };

    $.fn.successNotification = function (text, options, callback) {

        if ($.isFunction(options)) {
            callback = options;
            options = {};
        }

        $.fn.notification.call(this, text, customizedType(options, 'success', 'Well done!'), callback);
    };

    $.fn.warningNotification = function (text, options, callback) {

        if ($.isFunction(options)) {
            callback = options;
            options = {};
        }

        $.fn.notification.call(this, text, customizedType(options, 'warning', 'Warning!'), callback);
    };

    $.fn.dangerNotification = function (text, options, callback) {

        if ($.isFunction(options)) {
            callback = options;
            options = {};
        }

        $.fn.notification.call(this, text, customizedType(options, 'danger', 'Error!'), callback);
    };

    function customizedType(options, type, textPrefix) {
        options.type = type;

        if (!options.textPrefix) {
            options.textPrefix = textPrefix;
        }

        return options;
    }
})(jQuery);
