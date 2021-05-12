## 快速开始

1. 是用antd本身的Upload设置name=file aceept= xls xlsx

2. 引入ali-oss，阿里云的oss，后端返回的accessKeyId、accessKeySecret、stsToken、bucket，然后实例化Oss

3. client.multipartUpload 接收keyname(时间戳和名字)，file；返回结果json

4. 实例化一个let fileReader = new FileReader() ，然后在onload方法里解析file

5. 解析表格数据，引入xlsx插件XLSX.read方法，以二进制流方式取得Excel表格对象--workbook

6. workbook的Sheets遍历一下，然后用XLSX.utils.sheet_to_json把表格的数据提取出来

7. code

   ```js
    // 读取数据
       readData = (file, url) => {
           let fileReader = new FileReader()
           fileReader.onload = (e) => {
               let workbook
               let data = e.target.result
               try {
                   workbook = XLSX.read(data, { type: 'binary',
                       cellDates: true }) // 以二进制流方式读取得到整份excel表格对象   日期格式需要加上 cellDates: true  参数
               } catch (e) {
                   console.log('文件类型不正确:' + e)
                   message.error('解析文件出错：' + e.toString())
                   return
               }
               // 表格的表格范围，可用于判断表头是否数量是否正确
               console.log(workbook, 1)
               // 遍历每张表读取 ,现在只读第一张表
               let newData
               for (let sheet in workbook.Sheets) {
                   if (workbook.Sheets.hasOwnProperty(sheet)) {
                       let data = XLSX.utils.sheet_to_json(workbook.Sheets[sheet], {defval:''}) // defval 空默认为 ''
                       data=data.filter(de=>de.__EMPTY_1 !=='手机号') // filter 掉第一行
                       console.log(data, '***********打印data***********')
                       newData = this.formatData(data)
                       console.log(newData, '***********打印newData***********')
                   }
               }
               this.postData({ meta: { file_name: file.name, file_url: url }, items: newData })
           }
           fileReader.onerror = () => {
               message.error({
                   title: '读取数据失败',
                   onOk: () => {}
               })
           }
   
           // 以二进制方式打开文件
           fileReader.readAsBinaryString(file)
       }
   ```

   

