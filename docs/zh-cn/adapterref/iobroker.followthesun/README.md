---
translatedFrom: en
translatedWarning: 如果您想编辑此文档，请删除“translatedFrom”字段，否则此文档将再次自动翻译
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/zh-cn/adapterref/iobroker.followthesun/README.md
title: ioBroker。跟随太阳
hash: J/g7F0hU1yfdbMFD+ncBg6RxzgsDKkfV0mQEdpoqZwg=
---
![商标](../../../en/adapterref/iobroker.followthesun/admin/followthesun.png)

![NPM版本](http://img.shields.io/npm/v/iobroker.followthesun.svg)
![资料下载](https://img.shields.io/npm/dm/iobroker.followthesun.svg)
![安装数量（最新）](http://iobroker.live/badges/followthesun-installed.svg)
![安装数量（稳定）](http://iobroker.live/badges/followthesun-stable.svg)
![依赖状态](https://img.shields.io/david/HGlab01/iobroker.followthesun.svg)
![已知漏洞](https://snyk.io/test/github/HGlab01/ioBroker.followthesun/badge.svg)
![NPM](https://nodei.co/npm/iobroker.followthesun.png?downloads=true)

＃ioBroker.followthesun
![测试与发布](https://github.com/HGlab01/ioBroker.followthesun/workflows/Test%20and%20Release/badge.svg)

## Followthesun ioBroker适配器
该适配器根据地理区域计算当前的海拔高度和太阳方位角。另外，还存储了罗盘方向和太阳的运动（日出或日落）。
它使用配置中定义的地理位置。可以在实例首选项中定义计算间隔。
也会存储今天，明天或春季/夏季/秋季/冬季开始之类的几天的正午值。

## Changelog
<!--
    Placeholder for the next version (at the beginning of the line):
    ### __WORK IN PROGRESS__
-->
### __WORK IN PROGRESS__
* (HGlab01) 

### 0.2.2 (2020-12-07)
* (HGlab01) Decrease log-level

### 0.2.1 (2020-12-07)
* (HGlab01) update dependecies
* (HGlab01) add solar-noon information
* (HGlab01) add compass information
* (HGlab01) breaking change! states moved from root to "current"

### 0.1.0 (2020-11-30)
* (HGlab01) first beta release

### 0.0.7-0 (2020-07-21)
* (HGlab01) alpha version

## License
MIT License

Copyright (c) 2020 HGlab01 <iobroker.followthesun@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.