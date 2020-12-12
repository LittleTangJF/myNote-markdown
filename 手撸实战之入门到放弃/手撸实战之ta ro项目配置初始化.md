# taro

### 快速开始

####   安装

- 全局安装cli      Yarn global add @tarojs/cli
- 初始化              taro init app



### npm包

#### 	husky 代码规范

- ```js
  // yarn add -D husky lint-staged
  // package.json
  "husky": {
      "hooks": {
        "pre-commit": "lint-staged"
      }
    },
  "lint-staged": {
      "*.{ts,tsx}": [
        "eslint --fix"
      ]
    }
  ```

### 环境切换

- ```js
  const IS_MOCK = false
  const prefix = (): string => {
    if (process.env.NODE_ENV === 'development') {
      return 'https://lolita.chocloud.cn'
    }
    return 'https://saas.chocloud.cn'
  }
  const baseBrl = () => {
    if (IS_MOCK) {
      return 'http://127.0.0.1:9000/api'
    }
    return prefix() + '/lolita_api_v2/index.php'
  }
  ```

### Config

- ```
  // config index
  设置alias
  alias: {
      '@/assets': path.resolve(__dirname, '..', 'src/assets'),
      '@/config': path.resolve(__dirname, '..', 'src/config'),
      '@/enum': path.resolve(__dirname, '..', 'src/enum'),
      '@/components': path.resolve(__dirname, '..', 'src/components'),
      '@/service': path.resolve(__dirname, '..', 'src/service'),
      '@/utils': path.resolve(__dirname, '..', 'src/utils'),
      '@/actions': path.resolve(__dirname, '..', 'src/actions'),
      '@/constants': path.resolve(__dirname, '..', 'src/constants'),
      '@/enums': path.resolve(__dirname, '..', 'src/enums'),
      '@/reducers': path.resolve(__dirname, '..', 'src/reducers'),
      '@/store': path.resolve(__dirname, '..', 'src/store'),
      '@/typings': path.resolve(__dirname, '..', 'src/typings'),
      '@/style': path.resolve(__dirname, '..', 'src/style'),
      '@/pages': path.resolve(__dirname, '..', 'src/pages')
    },
  ```

  