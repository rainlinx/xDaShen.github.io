---
title: Maven踩坑心得
date: 2019-09-03 12:45:35
tags:
---
# Maven踩坑心得
1. 版本遵从就近原则：
	 A项目引用了B项目，则B项目中的版本号以A为准，特别是spring boot的starter-parent需要注意。
