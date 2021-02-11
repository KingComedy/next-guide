### 创建页面
+ 页面需要放置在pages文件夹下，每个文件就是一个页面
+ 页面组件需要被默认导出
+ 页面组件中不需要引入React
+ 页面地址与文件地址是对应关系
### 页面跳转
+ 使用Link组件跳转
```js
import Link from 'next/link'
<Link href="/list">
  <a title="go list">go list</a>
</Link>
```
+ 如果浏览器中JavaScript被禁用，则使用链接调整
+ Link组件只能添加href属性，其他属性应该添加到a标签上
+ Link组件在生产环境会通过预取功能自动优化应用程序以获取最佳性能
### 静态资源
+ 静态资源放于public文件夹
+ 组件通过'/image/*.jpg'可以直接访问
### 修改页面元数据
+ 通过Head组件修改元数据
```js
import Head from 'next/head'
<>
  <Head>
    <title>List page</title>
  </Head>
</>
```
### 使用css
+ next内置了style-jsx
```js
<style jsx>{`
  .class{
    color: blue
  }
`}</style>
```
### 添加全局样式
+ 在pages文件夹中新建_app.js文件，并加入以下代码
  ```js
  export default function App({ Component, pageProps}){
    return <Component {...pageProps}/>
  }
  ```
+ 在项目根目录下创建styles文件夹，并添加global.css文件
+ 在_app.js中引入global.css
### 预渲染
+ 指数据和html的拼接在服务器端提前完成
+ 预渲染可以使SEO更加友好
+ 可以带来更好的用户体验
### 两种预渲染形式：静态生成和服务器端生成
+ 静态生成：是在构建时已经生成HTML页面。后面的每个请求都共用构建时生成好的HTML
+ 服务器端渲染：服务器端渲染是在请求时生成HTML，每个请求都会重新生成HTML
### 静态生成
+ 需要提前的数据，要在getStaticProps方法里面获取
+ getStaticProps只在构建的时候执行