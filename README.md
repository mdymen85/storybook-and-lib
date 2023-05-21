# sbt-componentes
Storybook dos componentes da Suite

## What is Storybook?

Storybook is an open-source tool for developing and showcasing UI components in isolation for React and other front-end frameworks. It provides a sandbox environment to render and interact with UI components outside the context of the main application, allowing developers to test and showcase components in various states and configurations without having to navigate through the entire application.

With Storybook, you can create and manage a library of UI components and their documentation, and visualize and test them in different contexts, states, and props. You can use various addons and integrations to extend the functionality of Storybook, such as accessibility checks, automated testing, and design systems.

Here are some of the benefits of using Storybook in a React project:

Faster development: Storybook enables faster development by allowing developers to work on components in isolation, without worrying about the overall application or dependencies.

Improved collaboration: Storybook promotes collaboration and communication among developers, designers, and stakeholders by providing a shared and accessible platform to showcase and review components.

Better testing: Storybook provides a testing framework for UI components, allowing developers to test components in different states and configurations and catch bugs early in the development process.

Consistent design: Storybook helps maintain design consistency across the application by providing a single source of truth for UI components and their documentation.

Better documentation: Storybook generates documentation for components automatically, making it easier to understand how to use them and reducing the amount of time spent writing documentation.

To use Storybook in a React project, you need to install it as a dev dependency using a package manager like npm or yarn, and then configure and customize it according to your project needs. Once set up, you can create stories for your UI components in separate files and organize them in a hierarchy that reflects the structure of your application. You can then run Storybook in the browser to visualize and interact with the components in various states and configurations.

## Run it

```
npm run storybook
```

output example:

```
> sbt-componentes@1.0.0 storybook
> storybook dev -p 6006

@storybook/cli v7.0.9

info => Starting manager..
WARN You (or an addon) are using the 'config' preset field. This has been replaced by 'previewAnnotations' and will be removed in 8.0
info Addon-docs: using MDX2
info => Using implicit CSS loaders
info => Using default Webpack5 setup
<i> [webpack-dev-middleware] wait until bundle finished
<i> [webpack-dev-middleware] wait until bundle finished: /__webpack_hmr
╭───────────────────────────────────────────────────╮
│                                                   │
│   Storybook 7.0.9 for nextjs started              │
│   277 ms for manager and 13 s for preview         │
│                                                   │
│    Local:            http://localhost:6006/       │
│    On your network:  http://192.168.0.17:6006/    │
│                                                   │
╰───────────────────────────────────────────────────╯
<i> [webpack-dev-middleware] wait until bundle finished: /runtime~main.iframe.bundle.js
<i> [webpack-dev-middleware] wait until bundle finished: /vendors-node_modules_storybook_addon-essentials_dist_actions_preview_mjs-node_modules_storybo-57ad00.iframe.bundle.js
```

## How it works

In a Storybook app, files with names like button.stories.js and button.jsx are used to define and render UI components in isolation.

Here is what these files are for:

button.jsx: This file contains the implementation of the UI component. It is a regular React component written in JSX syntax. The button.jsx file defines the structure and behavior of the button component, and exports it so that it can be imported and used in other parts of the application.

button.stories.js: This file contains the stories for the button component. A Story is a representation of a UI component in a particular state. The button.stories.js file defines different stories for the button component, each showing it in a different state or with different props. For example, a story could show the button in its default state, with a particular color scheme, or with a different label. By defining multiple stories, you can test and showcase the behavior and appearance of the component in various scenarios.

Here is an example of what these files might look like:

button.jsx

```
function Button(props) {
  return (
    <button onClick={props.onClick} className={props.className}>
      {props.label}
    </button>
  );
}
```

button.stories.js

```
import React from 'react';
import { storiesOf } from '@storybook/react';
import Button from './button';

storiesOf('Button', module)
  .add('Default', () => <Button label="Click me!" />)
  .add('With Icon', () => <Button label="Click me!" icon={<i className="fa fa-search" />} />)
  .add('Disabled', () => <Button label="Click me!" disabled />)
  .add('Primary', () => <Button label="Click me!" className="btn-primary" />);

```  
  
In this example, the button.jsx file defines a simple button component that takes a label, className, and onClick prop. The button.stories.js file defines four stories for the button component: the default state, a state with an icon, a disabled state, and a primary state. Each story renders the button component with different props and shows how it appears and behaves in various scenarios.

## Axion 

You can make requests using the Axios library inside a component in a JSX file in React.

Axios is a popular JavaScript library used for making HTTP requests from a web browser or a Node.js server. It can be used to send GET, POST, PUT, DELETE, and other types of HTTP requests to a server, and receive and process the response.

To use Axios in a React component, you first need to install it as a dependency using a package manager like npm or yarn. You can then import it in your component and use it to make requests.

Here is an example of how you might use Axios to fetch data from a server inside a React component:

```
import React, { useState, useEffect } from 'react';
import axios from 'axios';

function MyComponent() {
  const [data, setData] = useState([]);

  useEffect(() => {
    axios.get('https://example.com/data')
      .then(response => setData(response.data))
      .catch(error => console.log(error));
  }, []);

  return (
    <div>
      {data.map(item => <div key={item.id}>{item.name}</div>)}
    </div>
  );
}

export default MyComponent;
```

In this example, the MyComponent function component uses the useState and useEffect hooks to manage a state variable called data, which initially contains an empty array. In the useEffect hook, Axios is used to make a GET request to a server URL and set the data state variable to the response data using the setData function. The catch block logs any errors that occur.

Finally, the data variable is mapped over to render a list of items, where each item has a unique id and a name.

Note that you should avoid making API requests inside the render method of a React component, as this can cause performance issues. Instead, you should use hooks like useEffect to make requests and update the state of the component.

## useState

useState is a hook provided by the React framework that enables state management in functional components. It allows you to define stateful values and their setters within the functional component, and React will take care of updating and re-rendering the component when the state changes.

Axios is a library used for making HTTP requests in JavaScript, and it doesn't have a useState function. However, you can use useState to manage the state of data retrieved from an HTTP request using Axios.

Here is an example of using useState with Axios to manage the state of data retrieved from an API endpoint:

```
import React, { useState, useEffect } from 'react';
import axios from 'axios';

function MyComponent() {
  const [data, setData] = useState([]);

  useEffect(() => {
    axios.get('https://jsonplaceholder.typicode.com/users')
      .then(response => setData(response.data))
      .catch(error => console.log(error));
  }, []);

  return (
    <div>
      <h1>Users</h1>
      <ul>
        {data.map(user => (
          <li key={user.id}>{user.name}</li>
        ))}
      </ul>
    </div>
  );
}
```

In this example, the useState hook is used to define a state variable named data and its setter function setData. The useEffect hook is used to make an HTTP GET request using Axios to retrieve data from the JSONPlaceholder API and set the data state variable with the response data. The empty dependency array ([]) passed to useEffect ensures that the HTTP request is only made once when the component mounts.

The retrieved data is then used to render a list of user names in the component. Whenever the data state variable changes, React will re-render the component with the updated data.

**Other example of useState for an object**

```
import React, { useState } from 'react';

function App() {
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    message: ''
  });

  const handleChange = event => {
    const { name, value } = event.target;
    setFormData(prevState => ({
      ...prevState,
      [name]: value
    }));
  };

  const handleSubmit = event => {
    event.preventDefault();
    console.log(formData);
    // send form data to the server
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input type="text" name="name" value={formData.name} onChange={handleChange} />
      </label>
      <label>
        Email:
        <input type="email" name="email" value={formData.email} onChange={handleChange} />
      </label>
      <label>
        Message:
        <textarea name="message" value={formData.message} onChange={handleChange}></textarea>
      </label>
      <button type="submit">Submit</button>
    </form>
  );
}

export default App;
```
The main goal is to analyse how userState can accept an object with special attributes.


## Publish lib

To publish a library in Node.js, you typically use the npm publish command. 

Make sure your library is properly configured with a valid package.json file. The package.json file should include necessary metadata such as the package name, version, description, dependencies, and entry point.
Build your library if necessary:

```
  npm build

```

This step is optional but commonly performed for production-ready releases. It involves running any required build processes (e.g., transpilation, bundling) to generate the distributable files.
Login to your npm account (if required):

If you haven't already, you need to create an account on the npm registry (https://www.npmjs.com) and authenticate yourself using the npm login command. This step is required for publishing packages to the public npm registry. If you're publishing to a private registry, follow the authentication process specific to that registry.

Publish your library:

In the root directory of your library project, run the following command to publish your library to the npm registry:

```

npm publish

```

The npm publish command packages and uploads your library to the npm registry, making it available for installation by others. During the publishing process, npm validates your package, including its metadata and dependencies, to ensure it meets the requirements. If the publishing is successful, your library will be accessible from the npm registry under the specified package name and version.

**Additional considerations:**

It's good practice to adhere to semantic versioning when updating your library's version number in the package.json file.
You can publish new versions of your library by incrementing the version number in the package.json file and repeating the npm publish command.
Remember that once a package is published, it becomes **publicly available**, and subsequent updates should follow appropriate versioning and release management practices to avoid breaking changes for existing users of your library.
