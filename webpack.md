### 基本开发环境

```shell
npm install webpack webpack-cli  -g
npm init    /*初始化*/
/*配置package.json*/
"scripts": {
    "build": "webpack --mode development --config ./scripts/webpack.config.js",
  },
  
npm i --save-dev html-webpack-plugin  /*自动生成html*/
npm install style-loader -D    /*编译css*/
npm install css-loader -D      /*编译css*/
npm install --save-dev mini-css-extract-plugin   /*生产独立的css*/

/*配置webpack.config.js*/
module.exports = {
    
    entry:  js
    output: js
    plugins: 
    module:

}


npm run build
```

### css预处理

```shell
npm install less-loader --save-dev
// loader重右往左走的

rules: [
            {
                test: /\.less$/,
                use: [
                    MiniCssExtractPlugin.loader, 'css-loader','less-loader',
                ],   /*用来编译less到css再到页面*/
            },
        ],
  
 'less-loader'也可以写成 {loader:'less-loader',option:{}}
```

为属性添加前缀

```shell
npm i -D postcss-loader autoprefixer
//做一个postcss.config.js
//在package。json中添加"browserlist" 
'根据提供的目标浏览器的环境来，智能添加css前缀，js的polyfill垫片,来兼容旧版本浏览器。避免不必要的兼容代码，以提高代码的编译质量'
```

### 处理图片资源

```shell
不同文件类型用不同loader
npm install file-loader --save-dev

 use: [
         {
            loader: 'file-loader',
            options: {
                      name: 'static/images/[name].[ext]', 
                      publicPath: '../../',    publicPath: '/',线上为根目录
               //打开浏览器看url哪个才是根目录         
         },
     },
 ],             
```

**name             //jpg的输出位置，以webpack输出的文件为根目录**
**publicPath   //输出后的js/css中引用的jpg地址为url(publicpath+name)**

```shell
npm install url-loader --save-dev
可以把文件转为base64
loader: 'url-loader',
options: {
     limit: 8192,
     name: 'static/images/[name].[ext]',
     publicPath: '/',
}
超出limit的话 按照file-loader处理
```

### 处理静态资源--Copy

```shell
npm install copy-webpack-plugin --save-dev

new CopyPlugin([
            { from:'src/photo', to: 'static' },
        ]),
      from 以项目目录为出发点  
      to  输出位置，以webpack输出的文件dist为为出发点
```

### babel

```shell
npm install -D babel-loader @babel/core @babel/preset-env webpack

rules: [
    {
      test: /\.m?js$/,
      exclude: /(node_modules|bower_components)/,
      use: {
        loader: 'babel-loader',
        options: {
          presets: ['@babel/preset-env']
        }
      }
    }
  ]
```

