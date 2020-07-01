# mocha-chai 测试 HelloWorld 组件

> vue-test-utils 官方文档：https://vue-test-utils.vuejs.org/zh/

```js
import HelloWorld from '@/components/HelloWorld.vue'
import Vue from 'vue'
import { expect } from 'chai'
import { mount } from '@vue/test-utils'

describe('测试HelloWorld组件', () => {
  it('测试msg属性, 能否正常显示, 原生', () => {
    const msg = 'hello world';
    const Constructor = Vue.extend(HelloWorld);
    const vm = new Constructor({
      propsData: {
        msg
      }
    }).$mount();

    const domInner = vm.$el.getElementsByTagName('h1')[0].innerHTML;
    expect(domInner).to.be.include(msg)
  });

  it('测试msg属性, 能否正常显示, vue-test-utils', () => {
    const msg = 'hello world';
    const wrapper = mount(HelloWorld, {
      propsData: { msg }
    })
    const domInner = wrapper.find('h1').text();
    expect(domInner).to.be.include(msg)
  });
})
```