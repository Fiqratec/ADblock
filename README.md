# Adi.js :no_entry_sign:
Lightweight jQuery plugin for Adblock detection

![Thumb](http://i.imgur.com/EihVW9a.jpg)

### ```bower install adi.js```

[See it in action](http://codepen.io/mariusbalaj/pen/MaEdpx)

### To install follow the steps (order is important):
  
  - Include ```jQuery```
  - Include ```advertisement.js``` and make sure ```jQuery.adblock = false;``` is inside the file
  - Include ```jquery.adi.js```
  - Call ```$.adi({ /* your options here */ })```


### Options
All parameters are optional.

|    Option     |       Type        |                        Description                        |
|---------------|-------------------|-----------------------------------------------------------|
| ```title```   | ```string/html``` | Modal's title                                             |
| ```content``` | ```string/html``` | Modal's description                                       |
| ```theme ```  | ```string```      | Available: ```light```, ```dark``` (default: ```light```) |


### Methods

|      Method      |                                                    Description                                                    |
|------------------|-------------------------------------------------------------------------------------------------------------------|
| ```active()```   | Callback function triggered when ```$.adblock``` is ```undefined```.<br> *Adblock is active*                      |
| ```inactive()``` | Callback function triggered when ```$.adblock``` is ```false```.<br> *Adblock is inactive*                        |
| ```onOpen()```   | Callback function triggered when modal is appended to ```document.body``` and ```display``` is set to ```block``` |
| ```onClose()```  | Callback function triggered when modal's ```display``` is set to ```none```                                       |

### Examples

#### Don't let user to see the content if adblock is active
```
$.adi({
  onClose: function(el) {
    /* refresh each time user close the modal */
    window.location.reload(true);
  }
});
```

#### Redirect 
```
$.adi({
  onClose: function(el) {
    window.location = 'http://some-website.com';
  }
});
```

#### Add animation to modal
```
$.adi({
  onOpen: function(el) {
    /* make the modal bounce in by adding animate.css classes on modal */
    el.find('.jquery-adi_content').addClass('animated bounceInDown')
  },
});
