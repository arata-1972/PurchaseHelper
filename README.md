
[![Build Status](https://travis-ci.org/exsortis/PurchaseHelper.svg?branch=master)](https://travis-ci.org/exsortis/PurchaseHelper) [![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage#adding-frameworks-to-an-application) [![Cocoapods compatible](https://img.shields.io/cocoapods/v/PurchaseHelper.svg?style=flat)](https://cocoapods.org/pods/PurchaseHelper) [![License: MIT](https://img.shields.io/cocoapods/l/PurchaseHelper.svg?style=flat)](http://opensource.org/licenses/MIT)

# PurchaseHelper
In-app purchase helper and UI elements

## Usage

### Helper

Instantiate the helper once, and keep a strong reference to it somewhere.

```
NSSet<NSString*>* productIds = [NSSet setWithObjects:@"product1", @"product2", @"product3"];
PurchaseHelper* helper = [[PurchaseHelper alloc] initWithProductIdentifiers:productIds keychainAccount:@"MyIAPs"];
```


### UI

Create the view controller, providing it a reference to the helper. Customize its appearance, then display it.

```
PurchasesViewController* vc = [PurchasesViewController new];
vc.purchaseHelper = helper;

vc.titleFont = appTitleFont;
vc.buttonFont = appButtonFont;
...

[self presentViewController:purchasesVC animated:YES completion:nil];
```

If your app needs to know when the purchase completed, setup a notification observer:

```
[[NSNotificationCenter defaultCenter] addObserverForName:ProductPurchasedNotification object:nil queue:nil usingBlock:^(NSNotification* note){
    NSString* productId = note.userInfo[ProductPurchasedNotificationProductIdentifierKey];
    // do something with the notification
}];
```

## Copyright

Copyright © 2016-7 Pilgrimage Software

## License

See [LICENSE](LICENSE) for details.
