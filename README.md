# ice-stark-demo

## 使用

`icestark-react-main`：React主应用

`icestark-react-child`：React子应用

`icestark-vue-child`：Vue子应用

环境
node版本：16.14.2

主应用路由配置

```javascript
// @ts-ignore
const appConfig: IAppConfig = {
  app: {
    rootId: 'icestark-container',
    addProvider: ({ children }) => (
      <ConfigProvider prefix="next-icestark-">{children}</ConfigProvider>
    ),
  },
  router: {
    type: 'browser',
  },
  icestark: {
    Layout: FrameworkLayout,
    getApps: async () => {
      const apps = [{
        path: '/seller',
        title: '商家平台',
        loadScriptMode: 'import',
        // React  对应 icestark-react-child 项目
        entry: 'http://localhost:3334/',
      }, {
        path: '/waiter',
        title: '小二平台',
        loadScriptMode: 'import',
        // Vue  对应 icestark-vue-child 项目
        entry: 'http://localhost:3000/',
      }, {
        path: '/angular',
        title: 'Angular',
        sandbox: true,
        // Angular 
        entry: 'https://iceworks.oss-cn-hangzhou.aliyuncs.com/icestark/child-common-angular/index.html',
      }];
      return apps;
    },
    appRouter: {
      LoadingComponent: PageLoading,
    },
  },
};
```

