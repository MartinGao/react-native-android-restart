# react-native-android-restart

A React-native component for android. Allows programmatically restarting the android app.

Supports React Native up to 0.21.

### Installation

```bash
npm install --save react-native-android-restart
```

### Add it to your android project

* In `android/setting.gradle`

```gradle
...
include ':RNRestartActionPackage'
project(':RNRestartActionPackage').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-android-restart)
```

* In `android/app/build.gradle`

```gradle
...
dependencies {
    ...
    compile project(':RNRestartActionPackage')
}
```

```java
import com.facebook.react.ReactActivity;
import com.facebook.react.ReactPackage;
import com.facebook.react.shell.MainReactPackage;

import java.util.Arrays;
import java.util.List;

import com.zamiang.RestartAction.RestartActionPackage; // <--- import

public class MainActivity extends ReactActivity {

   ...

   /**
   * A list of packages used by the app. If the app uses additional views
   * or modules besides the default ones, add more packages here.
   */
    @Override
    protected List<ReactPackage> getPackages() {
      return Arrays.<ReactPackage>asList(
        new MainReactPackage(),
        new RestartActionPackage(this)          // <------ add here
      );
    }
}

```

## Example
```javascript
import { NativeModules } from 'react-native';
import { restart } from NativeModules.RestartAction;

class App extends React.Component {

  restart() {
    restart();
  }

  render() {
    return (
      <View>
        <Button onClick={this.restart} "/>
      </View>
    );
  }
}

module.exports = App;
```

## License

MIT
