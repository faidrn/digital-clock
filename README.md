# Digital Clock

![](https://github.com/faidrn/digital-clock/blob/main/assets/images/ScreenShotDigitalClock.png)


Digital clock with HTML, CSS and JavaScript.

## HTML

This is the HTML structure:

```html
<div class="clock">
    <span id="time"></span>
</div>
```

### Clock

This div containt the clock.

### Time

This tag `span` is an inline container and it's used to apply style to text or group elements inline. In this project, it's the **clock**, because this tag will be used to show the time getting with JS.


## JavaScript

The next code is using to get the clock working:

```javascript
const setClock = () => {
    const now = new Date();
    const hours = String(now.getHours()).padStart(2, '0');
    const minutes = String(now.getMinutes()).padStart(2, '0');
    const seconds = String(now.getSeconds()).padStart(2, '0');
    const timeString = `${hours}:${minutes}:${seconds}`;

    document.getElementById('time').textContent = timeString;
};

setInterval(setClock, 1000);
setClock();
```

A function called **setClock** is declared using an arrow function (=>). This function will update the content of an HTML element with the id time to display the current time.

`const now = new Date()` Here a Date object is created that represents the current date and time.

Hours, minutes and seconds are extracted
```javascript
const hours = String(now.getHours()).padStart(2, '0');
const minutes = String(now.getMinutes()).padStart(2, '0');
const seconds = String(now.getSeconds()).padStart(2, '0');
```

* `now.getHours()` gets the current hour (0-23).
* `now.getMinutes()` gets the current minutes (0-59).
* `now.getSeconds()` gets the current seconds (0-59).

Each of these values ​​is converted to a `String()` and `padStart(2, '0')` is used to ensure that they always have at least two digits. If the number has only one digit, a '0' is added to the beginning. For example, if the hour is 9, it becomes "09".

With **const timeString = `${hours}:${minutes}:${seconds}`** a string is created in the format hh:mm:ss using template literals syntax.

With **document.getElementById('time').textContent = timeString** the HTML element with the id **time** is selected and its content (textContent) is updated with the formatted time string.

**setInterval(setClock, 1000)** sets up a timer that calls the setClock function every 1000 milliseconds (1 second). This ensures that the clock is updated every second.

Finally, the setClock function is called immediately (**setClock();**) so that the clock is updated when the page loads, without waiting for the first 1-second interval.