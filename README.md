# Module Config Helper for ProcessWire

## Usage

### Define a default array in your module:

```php
protected static $defaultConfig = array(

    // example with just one option
    'prettySetting'  => array(

        // the label for the form
        'label' => 'Pretty Setting',

        // the default value
        'value' => 'I am pretty',

        // optional, defaults to 'InputfieldText'
        'inputfieldType' => 'InputfieldText'
    ),

    // example with multiple options
    'awesomeSetting' => array(

        // the label for the form
        'label' => 'Awesome Setting',

        // the default value
        'value' => 2,

        // optional, defaults to 'InputfieldRadios'
        'inputfieldType' => 'InputfieldRadios',

        // each key is for the form label, each value will be saved if selected
        'options' => array(
            'Option 1' => 1,
            'Option 2' => 2,
            'Option 3' => 3
        ),

        // set any additional attribute to the input field
        "attributes" => array(
            "optionColumns" => 1
        )
    )
);
```

### Apply the defaults to your module:

```php
public function __construct() {
    PWModuleConfigHelper::apply($this, self::$defaultConfig);
}
```

### Render out the form:

```php
public static function getPWModuleConfigInputfields(array $data) {
    return PWModuleConfigHelper::renderForm($data, self::$defaultConfig);
}
```

#### Result:

![screenshot](http://i.imgur.com/QMjCVgh.png)



### Access any of the config settings from your module:

```php
$this->awesomeSetting;
```

### Version history

* v0.0.1 initial version

### ProcessWire

[processwire.com](http://processwire.com)

### License

This software is licensed under [The MIT License (MIT)](http://opensource.org/licenses/MIT)