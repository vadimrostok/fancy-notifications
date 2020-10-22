# Capacitor Fancy Notifications

## Installation

- `npm i vadimrostok/fancy-notifications`

## Usage


```typescript
import { Plugins } from '@capacitor/core';
const { FancyNotifications } = Plugins;
async function updateBadgeCount() {
  const check = await FancyNotifications.hasPermission();
  if (check.value) {
    FancyNotifications.setBadgeCount({ count: 2 });
  } else {
    const request = await FancyNotifications.requestPermission();
    if(request.value) {
      FancyNotifications.setBadgeCount({ count: 2 });
    } else {
      // User failed to grant permission show some dialog
    }
  }
}

```

### Android

In your `MainActivity.java` add import

```java
com.github.triniwiz.capacitor.notifications.FancyNotifications;
```

and add 

```java
add(FancyNotifications.class);
```

to your plugins list in onCreate.

## Api

| Method                                               | Default | Type                      | Description                 |
| ---------------------------------------------------- | ------- | ------------------------- | --------------------------- |
| hasPermission |         | `Promise<{value:boolean}>` |  |
| requestPermission |         | `Promise<{value:boolean}>` |  |
| setBadgeCount |         | `Promise<any>` |  |
| clearBadgeCount |         | `Promise<any>` |  |

## TODO

- [ ] Add Notifications Support
