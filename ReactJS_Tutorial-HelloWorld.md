# ReactJS Tutorial
By Edwin Tumbaga

### Requirements
- Hypervisor Environment Setup (VirtualBox / VMWare)
- CentOS8 / Rocky Linux
- Installed node.js
- Created ReactJS project using  `create-react-app` (sample project name of app I used is `myreactjsapp`, but the project name can be anything)
- Editor of choice (I use VS Code in my Windows/Linux setup, but VI or any Linux editor is fine)


### Getting Started

Go to your ReactJS project directory, and start the app
```
cd myreactjsapp
npm start
```
Open the URL indicated in the started service on your browser. The default ReactJS page should now be displayed
_NOTE: Replace the IP with the one provided by the started service_
```
http://192.168.1.149:3000 
```
# Hello World
On your project directory, go to the `src` folder, and, using your editor, open the `App.js` file
```
cd myreactjsapp/src
vim App.js
``` 
Replace the current code
```js
import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}

export default App;
```
with this one
```js
function App() {
  return (
    <div className="App">
      <h1>Hello World</h1>
    </div>
  );
}

export default App;
```

The browser will auto-refresh, and you should now have your Hello World in ReactJS :-)




