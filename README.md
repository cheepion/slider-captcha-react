## Captcha

[AJ-Captcha](https://gitee.com/anji-plus/captcha)  React版 ,界面优化调整 支持滑块和点选切换

![alt slide.png](https://raw.githubusercontent.com/cheepion/slider-captcha-react/master/src/assert/slide.png)

![alt point.png](https://raw.githubusercontent.com/cheepion/slider-captcha-react/master/src/assert/point.png)
https://raw.githubusercontent.com/cheepion/slider-captcha-react/master/src/assert/point.png

## Getting Started

Install dependencies,

```bash

$ yarn add slider-captcha-react

  // or
  
$ npm install slider-captcha-react
```

## API

| 属性        | 说明                                              | 类型     | 默认值                     |
| ----------- | ------------------------------------------------- | -------- | -------------------------- |
| onFail      | 校验失败时的函数回调                              | Function | -                          |
| onSuccess   | 校验成功时的函数回调,会将二次校验参数作为参数传递 | Function | -                          |
| type        | 显示校验模块的方式,可选 point(点选),slide(滑动)   | String   | auto                      |
| path        | 后端路径前缀                                      | String   | -                          |

## hooks

useCaptcha

```jsx
import React, { useRef } from 'react';
import { useCaptcha } from 'slider-captcha-react';

export default () => {
  const [run] = useCaptcha({ path: 'http://foo.com', type: 'auto' });

  const click = async () => {
    const data = await run()
    console.log(data)
  };

  return (<button onClick={click}>verify</button>);
}

```

## Demo

```jsx
import React, { useRef } from 'react';
import { Captcha } from 'slider-captcha-react';

export default () => {
  const ref = useRef();

  const click = () => {
    ref.current?.verify();
  };

  return (
    <Captcha
      onSuccess={(data) => console.log(data)}
      path='https://api.xxx.com'
      type='auto'
      ref={ref}
    >
      <button
        onClick={click}
        style={{
          border: 'none',
          color: '#fff',
          width: '100px',
          height: '50px',
          lineHeight: '50p',
          background: '#1890ff',
        }}
      >
        点击
      </button>
    </Captcha>
  );
}

```
