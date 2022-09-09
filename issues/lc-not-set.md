## Error
OS: Archlinux 

```
...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = "en_US.UTF-8",
	LC_CTYPE = "en_US.UTF-8",
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
...
```
## Solution

I had mistakenly set the locale to some esoteric choice. To solve I modified the `/etc/locale.gen`. Leaving uncommented only the `en_US.UTF-8 UTF-8`, commenting the previous active locale (`uk_UA.UTF-8 UTF-8`) and running `locale-gen` did the trick.

### References:
[Archwiki on Locale](https://wiki.archlinux.org/title/Locale)
