# basic-react-template


##Pre-Installation

 - Node
 - Yarn ... if using yarn as global package manager

........ Basic Installation ............:

 - npm init
 - npm i -D webpack webpack-dev-server
 - npm i -g webpack webpack-dev-server
 - npm i -S react react-dom
 - npm i -D babel-loader babel-core babel-preset-es2015 babel-preset-react
 - npm i -D html-webpack-plugin (To load the bundeled file created by Babel Loaders
				 dynamically in the index.html file)

........Configuring some basic files .............

 - create webpack.config.js file
	const path = require('path');
	const HtmlWebpackPlugin = require('html-webpack-plugin');
	const HtmlWebpackPluginConfig = new HtmlWebpackPlugin({
	template: './client/index.html',
    	filename: 'index.html',
    	inject: 'body'
	});

	module.exports = {
  		entry: './client/index.js',
  		output: {
    			path: path.resolve('dist'),
    			filename: 'index_bundle.js'
  		},
  		module: {
    			loaders: [
      				{ test: /\.js$/, loader: 'babel-loader', exclude: /node_modules/ },
      				{ test: /\.jsx$/, loader: 'babel-loader', exclude: /node_modules/ }
    			]
  		},
    		plugins: [HtmlWebpackPluginConfig]
	}

- create .babelrc file

		{
    			"presets":[
      			"es2015", "react"
    			]
		}

- create 'client' folder
- inside client create - index.js and index.html
	- inside index.js ..... write something, like console.log("hey");
	- create a basic intex.html file and add following inside body tag:
		<div id="root"></div>

.......... Starting Webpack for local dev .........

- add "start": "webpack-dev-server" .. under "scripts" of package.json
- run npm start
- go to http://localhost:8080
- console should log "hey"


............. Createing first Component ..........

- create "component" directory under client
- create "App.jsx" file inside component ..... (using PascalCase is standart for naming)

	import React from 'react';

	export default class App extends React.Component {
  		render() {
    			return (
     				<div style={{textAlign: 'center'}}>
        				<h1>Hello World</h1>
      				</div>);
  		}
	}

- update index.js with following
 	import React from 'react';
	import ReactDOM from 'react-dom';
	import App from './componets/App.jsx';

	ReactDOM.render(<App />, document.getElementById('root'));

- Go to http://localhost:8080 and validate the "Hello World" h1 tag
