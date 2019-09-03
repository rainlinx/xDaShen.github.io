---
layout: spring
title: SpringBoot与axios遇到的坑
date: 2019-09-03 12:43:18
tags:
---
spring boot:
1. @RequestParam
	- 适用于content-type不等于application/json的post请求，post请求需要用qs.stringify()序列化数据
	- 适用于get请求（好像只能传基本类型）
2.  @RequestBody
	- 适用于content-type等于application/json的post请求

axios:
1. get
```javascript
axios.get(
'/api',
{
	params: { //必须要这么写
	
})
```
2. post
```javascript
axios.post(
'/api',
{}或者params//参数名随意)
```
