---
title: "新拟态设计实例"
linkTitle: "新拟态设计实例"
slug: "neumorphism"
date: 2022-10-05T16:49:28+08:00
draft: false
tags: ["前端"]
categories: []
summary: "也许是一个好的设计风格"
---

<style>
  .JHg5Z4WNTEgbc7jpsZB7-wrapper-bg {
    background: #eeeeee;
    border-radius: 20px;
    padding: 50px 20px;
  }
  .JHg5Z4WNTEgbc7jpsZB7-wrapper {
    width: 100%;
    display: flex;
    justify-content: space-around;
    align-items: flex-end;
    flex-wrap: wrap;
    margin-top: 10px;
  }

  .JHg5Z4WNTEgbc7jpsZB7-wrapper .JHg5Z4WNTEgbc7jpsZB7-item1,
  .JHg5Z4WNTEgbc7jpsZB7-wrapper .JHg5Z4WNTEgbc7jpsZB7-item2,
  .JHg5Z4WNTEgbc7jpsZB7-wrapper .JHg5Z4WNTEgbc7jpsZB7-item3,
  .JHg5Z4WNTEgbc7jpsZB7-wrapper .JHg5Z4WNTEgbc7jpsZB7-item4,
  .JHg5Z4WNTEgbc7jpsZB7-wrapper .JHg5Z4WNTEgbc7jpsZB7-item5,
  .JHg5Z4WNTEgbc7jpsZB7-wrapper .JHg5Z4WNTEgbc7jpsZB7-item6,
  .JHg5Z4WNTEgbc7jpsZB7-wrapper .JHg5Z4WNTEgbc7jpsZB7-item7,
  .JHg5Z4WNTEgbc7jpsZB7-wrapper .JHg5Z4WNTEgbc7jpsZB7-item8,
  .JHg5Z4WNTEgbc7jpsZB7-wrapper .JHg5Z4WNTEgbc7jpsZB7-item9-outer {
    margin-left: 40px;
  }

  .JHg5Z4WNTEgbc7jpsZB7-item1 {
    width: 80px;
    height: 80px;
    border-radius: 20px;
    background: #eeeeee;
    box-shadow: 10px 10px 15px #dddddd, -10px -10px 15px #ffffff;
    margin: 10px;
  }

  .JHg5Z4WNTEgbc7jpsZB7-item2 {
    width: 120px;
    height: 120px;
    border-radius: 30px;
    background: #eeeeee;
    box-shadow: 15px 15px 22.5px #dddddd, -15px -15px 22.5px #ffffff;
    margin: 15px;
  }

  .JHg5Z4WNTEgbc7jpsZB7-item3 {
    width: 160px;
    height: 160px;
    border-radius: 40px;
    background: #eeeeee;
    box-shadow: 20px 20px 30px #dddddd, -20px -20px 30px #ffffff;
    margin: 20px;
  }

  .JHg5Z4WNTEgbc7jpsZB7-item4 {
    width: 200px;
    height: 200px;
    border-radius: 50px;
    background: #eeeeee;
    box-shadow: 25px 25px 37.5px #dddddd, -25px -25px 37.5px #ffffff;
    margin: 25px;
  }

  .JHg5Z4WNTEgbc7jpsZB7-item5 {
    width: 240px;
    height: 240px;
    border-radius: 60px;
    background: #eeeeee;
    box-shadow: 30px 30px 45px #dddddd, -30px -30px 45px #ffffff;
    margin: 30px;
  }

  .JHg5Z4WNTEgbc7jpsZB7-item6 {
    width: 120px;
    height: 80px;
    border-radius: 20px;
    background: #eeeeee;
    box-shadow: 10px 10px 15px #dddddd, -10px -10px 15px #ffffff;
    margin: 10px;
  }

  .JHg5Z4WNTEgbc7jpsZB7-item7 {
    width: 80px;
    height: 80px;
    border-radius: 80px;
    background: #eeeeee;
    box-shadow: 10px 10px 15px #dddddd, -10px -10px 15px #ffffff;
    margin: 10px;
  }

  .JHg5Z4WNTEgbc7jpsZB7-item8 {
    width: 200px;
    height: 120px;
    border-radius: 80px 40px 20px 0;
    background: #eeeeee;
    box-shadow: 15px 15px 22.5px #dddddd, -15px -15px 22.5px #ffffff;
    margin: 15px;
  }

  .JHg5Z4WNTEgbc7jpsZB7-item9 {
    width: 120px;
    height: 100px;
    content: "";
    background: #eeeeee;
    clip-path: path(
      "M40 100C20 100 10.2 83 24 60L45.6 24C60 0 60 0 74.4 24L96 60C109.8 83 100 100 80 100Z"
    );
  }

  .JHg5Z4WNTEgbc7jpsZB7-item9-outer {
    margin: 15px;
    filter: drop-shadow(12px 12px 8px #dddddd)
      drop-shadow(-12px -12px 8px #ffffff);
  }
</style>
<div class="JHg5Z4WNTEgbc7jpsZB7-wrapper-bg">
  <div class="JHg5Z4WNTEgbc7jpsZB7-wrapper">
    <div class="JHg5Z4WNTEgbc7jpsZB7-item1"></div>
    <div class="JHg5Z4WNTEgbc7jpsZB7-item2"></div>
    <div class="JHg5Z4WNTEgbc7jpsZB7-item3"></div>
    <div class="JHg5Z4WNTEgbc7jpsZB7-item4"></div>
    <div class="JHg5Z4WNTEgbc7jpsZB7-item5"></div>
  </div>
  <div class="JHg5Z4WNTEgbc7jpsZB7-wrapper">
    <div class="JHg5Z4WNTEgbc7jpsZB7-item8"></div>
    <div class="JHg5Z4WNTEgbc7jpsZB7-item7"></div>
    <div class="JHg5Z4WNTEgbc7jpsZB7-item6"></div>
    <div class="JHg5Z4WNTEgbc7jpsZB7-item9-outer">
      <div class="JHg5Z4WNTEgbc7jpsZB7-item9"></div>
    </div>
  </div>
</div>
