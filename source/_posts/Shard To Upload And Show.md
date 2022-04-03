---
title: 切片上传以及展示
catalog: true
comments: true
date: 2022-04-03 17:52:54
header-img: snail-bg.jpg
tags:
  - js
categories:
  - upload

---

## 切片上传

```js
// input为用户已经上传文件的input框
btn.onclick = async () => {
  const file = input.files[0]
  const [fileName,etc] = file.name.split('.')
  const size = 1024
  let index = 0
  while (true) {
    if (index * size > file.size) break
    const chunk = file.slice(index * size, (index + 1) * size)
    const chunkFile = new File([chunk],`${fileName}_${index}.${etc}`)
    index++
    const form = new FormData();
    form.append('file', chunkFile);
    await axios.post('/upload',form,{
      Headers: {
        contentType: 'multipart/form-data'
      }
    })
  }
}
```

## 图片不同方式展示

```js
show_btn.onclick = () => {
  const file = input.files[0]
  const [fileName,etc] = file.name.split('.')
  
  // blob转url
  img.src = window.URL.createObjectURL(file)
  img.title = fileName

  // base64
  const reader = new FileReader()
  reader.readAsDataURL(file)
  reader.onload = (e) => {
    console.log(e.target.result)
    img.src = e.target.result
  }

  // iframe展示pdf
  iframe.src = window.URL.createObjectURL(file)
}
```