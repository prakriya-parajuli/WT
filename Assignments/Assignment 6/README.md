Explain event bubbling and capture with an example.
Deadline:11th Jan, 8 am

# Bubbling in javascript:
While developing a webpage or a website via JavaScript, the concept of event bubbling is used where the event handlers are invoked when one element is nested on to the other element and are part of the same event. This technique or method is known as Event Bubbling. Thus, while performing event flow for a web page, event bubbling is used. We can understand event bubbling as a sequence of calling the event handlers when one element is nested in another element, and both the elements have registered listeners for the same event. So beginning from the deepest element to its parents covering all its ancestors on the way to top to bottom, calling is performed.

-> Example of event bubbling:
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Event Bubbling</title>
    <style>
        * {
            box-sizing: border-box;
        }
        
        div {
            width:100%;
            padding: 100px;
        }
        
        div:hover {}
        
        .one {
            background-color: rgba(101, 224, 252, 0.732);
            text-align: center;
            font-size: xx-large;
            font-weight: bolder;
        }
        
        .one:hover {
            box-shadow: 11px 13x 0px 0px rgba(255, 117, 79, 0.75);
        }
        
        .two {
            background-color: rgb(241, 156, 226);
        }
        
        .two:hover {
            box-shadow: 11px 13px 0px 0px rgba(79, 255, 232, 0.75);
        }
        
        .three {
            background-color: rgb(126, 165, 255);
        }
        
        .three:hover {
            box-shadow: 11px 13px 0px 0px rgba(79, 255, 232, 0.75);
        }
    </style>
</head>
<body>
    <div class="one"> One
        <div class="two">Two
            <div class="three">Three
            </div>
        </div>
    </div>
    <script>
        const divs = document.querySelectorAll('div');

        function logtext(e) {
            alert(this.classList.value);
            //e.stopPropagation();

        }
        divs.forEach(div => div.addEventListener('click', logtext, {
            capture: false
        }))
    </script>
</body>
</html>

# Capturing in javascript:
Event Capturing is opposite to event bubbling, where in event capturing, an event moves from the outermost element to the target. Otherwise, in case of event bubbling, the event movement begins from the target to the outermost element in the file. Event Capturing is performed before event bubbling but capturing is used very rarely because event bubbling is sufficient to handle the event flow.The three phases of event propagation are: capturing, target, and bubbling.Event capturing is rarely used and, usually, events are handled on bubbling.

->Example of event capturing:
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Event Capturing</title>
    <style>
        * {
            box-sizing: border-box;
        }
        
        div {
            width: 100%;
            padding: 100px;
        }
        
        .one {
            background-color: rgb(86, 255, 162);
            text-align: center;
            font-size: xx-large;
            font-weight: bolder;
        }
        
        .two {
            background-color: rgb(143, 102, 255);
        }
        
        .three {
            background-color:pink;
        }
    </style>
</head>

<body>
    <div class="one"> One
        <div class="two">Two
            <div class="three">three
            </div>
        </div>
    </div>
    <script>
        const divs = document.querySelectorAll('div');

        function logtext(e) {
            alert(this.classList.value);
            //e.stopPropagation();

        }
        divs.forEach(div => div.addEventListener('click', logtext, {
            capture: true
        }))
    </script>
</body>
</html>