# react-native-starterpack

### Getting Started
Install NPM and Node - To-Do

Install Expo CLI

Expo CLI is a command line tool that allows you to easily build, run, and deploy React Native applications.

To install Expo CLI, run the following command in your terminal:

    npm install -g expo-cli

To install Expo SDK, which is a collection of libraries that provide access to native device functionality, run the following command in your terminal (we'll be using version 48 for this hackpack)

    npm install expo@48 -g
----------
### Create a new project

To create a new project, run the following command in your terminal:

    npx create-expo-app my-app
    
This will create a new directory called my-app with all the files you need to get started. 

Feel free to replace my-app with your own project name. For the purposes of this starter pack, we will refer to the project name as my-app.

<br>

To run the application, run the following command in your terminal:

    cd my-app
    npm start
    
With Expo, you can directly run your application on your phone. To do so, 

1. Download the Expo app on your phone.
2. Once you have the Expo app, you can scan the QR code that appears in your terminal using the camera app or the built in QR code scanner in the Expo app.

Notes: There will be several additional files in the my-project directory that tell Expo how to build and run your application. You can ignore these files for now.

------
### Hello World!

1. Open the App.js file inside the my-app folder using a code editor of your choice. You should see the following code:

```js
import { StatusBar } from 'expo-status-bar';
import { StyleSheet, Text, View } from 'react-native';

export default function App() {
  return (
    <View style={styles.container}>
      <Text>Open up App.js to start working on your app!</Text>
      <StatusBar style="auto" />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
});
```

2. Replace the Text with component with the following:
```js
<Text>Hello World!</Text>
```

3. You should see the text "Hello World!" appear in the Expo app on your phone through live reloading.

----
### Styling

1. Observe the following code block at the bottom of App.js
```js
<View style={styles.container}>
  <Text>Hello World!</Text>
  <StatusBar style="auto" />
</View>
```
We can see that style attribute of the View tag is set to styles.container

Now look the definition of style at the bottom of file.
```js
const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
});
```

The const styles is declared as a StyleSheet object. This object contains a number of properties that describe how a component should be styled. Each property contains a number of key-value pairs. The key is the name of the style property aka the class, and the value is the value of the style property. For example, the backgroundColor property sets the background color of the component. The value of the backgroundColor property is '#fff', which is a hex code that represents white. Notice how these properties are camelCased versions of CSS properties.

2. Let's change the background colour to light blue. Change the background colour property to '#add8e6', and save the file. You should see the background colour change on your phone.

---
### Componenets

Components are sets for reusable code that can be used to minimize repetitive code in your project. There are functional and class based components, each with their own pros and cons. For this tutorial, we will be using functional components. 

Think of components like functions in a python script, for example, if you are writing a program where you are adding numbers many times, it makes more sense to create a function that adds two numbers, and call it wherever necessary. This makes the code more readable and manageable.

Similarly, if your application uses a button in many places, it's easier to create a button component, and call it wherever necessary.

Now, let's create a component.

1. Create a folder inside the my-app directory called `components`. Inside the components folder, create a file called `button.component.jsx`
2. Open the `button.component.jsx` file, and paste the following code block.

```js
import { TouchableOpacity, Text } from 'react-native';

const Button = () => {
  return (
    <TouchableOpacity onPress={() => console.log('Button Pressed!')}>
      <Text>Click Me!</Text>
    </TouchableOpacity>
  );
};

export default Button;
```

3. Import the button component into App.js using the following line:
```js
import Button from './component/button.component';
```

4. Add the button component after the text. You should see the button appear in the Expo app on your phone
```js
<Text>Hello World!</Text>
<Button />
```

You should now see the text 'Click Me!' below 'Hello World!', and should be able to click it. But it doesn't look like a button, and there is nothing the button does at the moment. To make these changes, we can add props to the component. Think of props like parameters to a functions. It allows you to customize the behaviour of a component each time you call it. 

5. Let's add some props, namely title, onPress, and style. This will allow us to dynamically change the title, onPress function, and style of the button.
```js
const Button = (props) => {
  return (
    <TouchableOpacity
      onPress={props.onPress}
      style={props.style}>
      <Text>{props.title}</Text>
    </TouchableOpacity>
  );
};
```

6. Now, we can customize the button in App.js.
```js
export default function App() {
  return (
    <View style={styles.container}>
      <Text>Hello World!</Text>
      <Button
        title='Click Me!'
        onPress={() => console.log('Button Pressed!')}
        style={styles.button}
      />
      <StatusBar style="auto" />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#add8e6',
    alignItems: 'center',
    justifyContent: 'center',
  },
  button: {
    backgroundColor: '#00bfff',
    padding: 10,
    borderRadius: 15,
    margin: 10,
  },
});
```
