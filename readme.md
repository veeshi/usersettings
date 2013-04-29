# UserSettings

## Portable Local Settings Storage for Python

- Automatic storage of settings information in a simple flat text file ([ConfigParser][] format)
- Automatically stored in an OS-appropriate location. For example, on OS X, the settings for an app with the chosen identifier "`com.example.apps.UserSettingsTest`" would be stored in `~/Library/Application Support/com.example.apps.UserSettingsTest/settings.cfg`
- Interface modeled on the [argparse][] module.

## Example:

The following example code shows the entire interface. This program will change its output each time it is run.

```
from UserSettings import UserSettings

#### Choose identifier for your app
CONF = UserSettings('com.example.apps.UserSettingsTest')

#### Create the individual settings keys, types, and default values
CONF.add_setting("counter", int, default=0)
CONF.add_setting("floatie", float, default=3.14159)
CONF.add_setting("stringie", str, default="s")
CONF.add_setting("boolie", bool, default=True)

#### Load any stored settings that might exist
CONF.load_settings()

#### Access the settings like attributes
print "Counter:",  CONF.counter
print "Floatie:",  CONF.floatie
print "Stringie:", CONF.stringie
print "Boolie:",   CONF.boolie
CONF.counter += 1
CONF.floatie *= 2
CONF.stringie = CONF.stringie + str(CONF.counter)
CONF.boolie = not CONF.boolie

#### Optionally save any changes
CONF.save_settings()
```

## License

This module is licensed under a BSD-style licence. See license.txt for details.

## To do

- Make into a proper python package
- Add to pypi

## Notes

- *Not yet a proper python package.*
- Requires the [appdirs][] module from pypi. 


[ConfigParser]: http://docs.python.org/2/library/configparser.html
[argparse]: http://docs.python.org/2/library/argparse.html
[appdirs]: https://pypi.python.org/pypi/appdirs