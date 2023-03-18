# lehttp_overrides

A Flutter package to resolve Let's Encrypt SSL certificate problems with Android 7.1.1 and below.

``` Note: This doesn't affect devices with android OS above 7.1.1 ```


More information [here](https://www.tomsguide.com/news/internet-disconnect-sept-30)

## Getting Started

To enable the fix you need to add this line at the beginning of your  project:

```dart
import 'package:lehttp_overrides/lehttp_overrides.dart';

void main() {
  if (Platform.isAndroid ) {
    HttpOverrides.global = LEHttpOverrides();
  }
  runApp(const MyApp());
}
```
This works if you are using **ISRG Root X1** certificate path
by adding **ISRG Root X1** CA to certificate store.

An optional parameter of the constructor `allowExpiredDSTX3` (defaults: false)
allows to accept as valid the **DST Root CA X3** expired certificate.
OpenSSL >= 1.1 should not trigger this check, but old Android versions still need it.

My suggestion is to leave this disabled and use **ISRG Root X1** certiicate path.
