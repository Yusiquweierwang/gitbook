[toc]

- `+`表示 public;
- `-`表示 private;
- `#`表示 protected;
- 不带符号表示 default;

**具体类**
![Alt text](https://pic4.zhimg.com/80/v2-71b22158f5b09dffa57a123d72ec4653_720w.webp)

**抽象类**
类名 / 方法——斜体
![Alt text](https://pic2.zhimg.com/80/v2-5c69cd9ff703377f7bbf37cee8199451_720w.webp)

**接口**
![Alt text](https://pic2.zhimg.com/80/v2-e39bdff5514c38e7797848372ac51365_720w.webp)

**包**
![ ](https://pic3.zhimg.com/80/v2-b421c9c15219feba7dd9cf7681070682_720w.webp)

## 关系

![Alt text](https://pic4.zhimg.com/80/v2-e6a48521352fff8270e753ea4a79d9fb_720w.webp)

### 实现关系

### 泛化关系-generalization

对象间继承关系
![Alt text](https://pic1.zhimg.com/80/v2-616c153ec74d496a811ac50c83c3653c_720w.webp)

### 关联关系-association

- 单向关联
  只有一个对象知道另一个对象（即可以调用）另一个对象的公共属性和操作。
- 双向关联

![Alt text](https://pic4.zhimg.com/80/v2-3f331f3dc075abb4215413014688638f_720w.webp)

- 数字：精确的数量
- _或者 0.._：表示 0 到多个
- 0..1：表示 0 或者 1 个，在 Java 中经常用一个空引用来实现
- 1..\*：表示 1 到多个

**关联关系分为依赖关联、聚合关联和组合关联**

- 依赖关系 dependency--弱关联
