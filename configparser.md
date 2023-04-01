- #python
- 示例文件`example.ini`
- ```
  [DATABASE]
  host = localhost
  port = 3306
  username = root
  password = password123
  
  [SERVER]
  host = 127.0.0.1
  port = 8000
  ```
- 导入`configparser`模块
	- ```python
	  import configparser
	  ```
- 创建`configparser`对象
	- ```python
	  config = configparser.ConfigParser()
	  ```
- 文件读写
  collapsed:: true
	- `read()`读取配置文件
		- ```python
		  config.read('example.ini')
		  ```
	- `write()`将修改后的配置写入`example.ini`
		- ```python
		  config.write(open('example.ini', 'w'))
		  ```
- 参数读写
	- `get()`获取`example.ini`中`DATABASE`中`host`的值保存至`db_host`变量
		- ```python
		  db_host = config.get('DATABASE', 'host', fallback=3306)
		  ```
		- `get`可能会抛出异常，所以可以使用`get`的第三个参数作为默认值
			- 如果该配置项不存在，则返回默认值`3306`
	- `getint()`获取`SERVER`中`port`的值保存至`server_port`变量
		- ```python
		  server_port = config.getint('SERVER', 'port')
		  ```
	- `items()`获取`example.ini'中`DATABASE`中所有的配置项
		- ```python
		  db_config = config.items('DATABASE')
		  ```
	- `set`修改`example.ini`中`SERVER`部分的`port`配置项为`8080`
		- ```python
		  config.set('SERVER', 'port', '8080')
		  ```
- 新建参数
	- `set()`向`example.ini`中添加一个新的部分`NEW_SECTION`并添加两个配置项`option1`和`option2`
		- ```python
		  config.add_section('NEW_SECTION')
		  config.set('NEW_SECTION', 'option1', 'value1')
		  config.set('NEW_SECTION', 'option2', 'value2')
		  ```
- 删除参数
	- `remove_section`删除`example.ini`中的`NEW_SECTION`部分
		- ```python
		  config.remove_section('NEW_SECTION')
		  ```
- 判断
	- `has_section()`判断`example.ini`中是否存在`DATABASE`部分
		- ```python
		  has_database = config.has_section('DATABASE')
		  ```
	- `has_option()`判断`example.ini`中`SERVER`部分是否存在`host`配置项
		- ```python
		  has_host = config.has_option('SERVER', 'host')
		  ```
-