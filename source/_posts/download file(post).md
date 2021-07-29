---
title: post请求下下载文件的方法
catalog: true
comments: true
header-img: snail-bg.jpg
tags:
- vue
---
如果后端是用post请求并且返回文件流可以采用以下代码

```js
  this.$api.post( url, { params }, { responseType: 'blob' })
    .then((res) => {
      // 触发下载
      const filename = res.headers['content-disposition'].replace('attachment; filename=', '').replace(/\"/g, '')
      const downloadElement = document.createElement('a')
      const href = window.URL.createObjectURL(res.data)
      downloadElement.href = href
      downloadElement.download = filename
      document.body.appendChild(downloadElement)
      downloadElement.click()
      document.body.removeChild(downloadElement)
    })
    .catch((err) => {
      this.$message.error('下载失败,' + err)
  })
```