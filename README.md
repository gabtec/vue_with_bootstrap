# How to use Bootstrap v3.3.7 in a Vue.js project

>1. Create a Vue Project with vue.cli
$ vue init webpack-simple demoProj
  -> accept the use of SASS

$ cd demoProj
$ npm install

>2. Install needed dependencies
$ npm install --save-dev url-loader
$ npm install --save jquery bootstrap@3	

>3. Open Vue.js 'main.js' file and import libs

	import 'jquery';
	import './utils/bootstrap/js/bootstrap.min.js';
	import './utils/bootstrap/css/bootstrap.min.css';

>4. Optimize webpack.config.js file to manage the new dependencies, by addind this to the existing file:

  module:
  {
    test: /\.(woff2?|eot|ttf|otf)(\?.*)?$/,
    loader: 'url-loader',
    query: {
      limit: 10000,
      name: 'fonts/[name].[ext]'
    }
  },

  plugins:[
    new webpack.ProvidePlugin({   
        jQuery: 'jquery',
        $: 'jquery',
        jquery: 'jquery'
    })
  ],

>5. Start the dev server
$ npm run dev