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

        // each key is for the input label, each value will be saved if selected
        'options' => array(
            'Option 1' => 1,
            'Option 2' => 2,
            'Option 3' => 3
        ),

        // set any additional attribute to the input field
        'attributes' => array(
            'optionColumns' => 1
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

### Stuff to be aware of

If you're using this in your module and you don't want it to clash with other modules using it, you have the following options to include it:

1. use ```spl_autoload_register``` to autoload it, so it only gets loaded once
2. only include the class if it has not been loaded yet, via ```class_exists('PWModuleConfigHelper')```
3. Option 1 and 2 require the class not to change (updates etc.) so the following options are more stable:
4. Namespace to class via renaming it, prefixing it with you module's name
5. Namespace it with PHP namespaces
6. I could make a module out of this but this might be overkill

### Version history

* v0.0.1 initial version

### ProcessWire

[processwire.com](http://processwire.com)

### License

This software is licensed under [The MIT License (MIT)](http://opensource.org/licenses/MIT)