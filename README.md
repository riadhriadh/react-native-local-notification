# react-native-local-notification

A package for React Native apps to show in-app notifications. Only tested on iOS but should work on Android.

# Demo
![local_notification](https://cloud.githubusercontent.com/assets/6998447/22668160/fd930aa2-ecbf-11e6-9a0b-ee03b505ed18.gif)

# Usage
```
<LocalNotification
  text="My awesome notification text"
  onNotificationPress={() => alert('pressed')}
  onNotificationHide={() => alert('hidden')}
/>
```

### Use with RN push notification
Example for use with React Native PushNotificationIOS.
```
onReceiveNotification(notification){
  this.setState({
    notifications: [...this.state.notifications, {
      text: 'My awesome notification text',
      onPress: () => alert('pressed'),
      onHide: this.onNotificationHide,
    }],
  });
}

onNotificationHide() {
  this.setState({
    notifications: this.state.notifications.slice(0, -1),
  });
}

render(){
  return (
    <View>
      {this.state.notifications.map((item, i) => (
          <LocalNotification
            key={i}
            text={item.text}
            onNotificationPress={item.onPress}
            onNotificationHide={item.onHide} />
        ))}
    </View>
  );
}
```

### Available props

Name | Type | Required | Default
--- | --- | --- | ---
text | `string` | Yes | Hello 👋🏼
duration | `number` | Yes | 3500
startHeight | `number` | Yes | 46
onNotificationPress | `func` | No | `NULL`
onNotificationWillShow | `func` | No | `NULL`
textStyle | `object` | No | {}
handleStyle | `object` | No | {}
notificationStyle | `object` | No | {}
ellipsizeTextStyle | `object` | No | {}