# 根据不同文件(.git)路径，切换不同 git 账户

## 1. 为每个github账户 设置 SSH 链接
1. 生成 SSH 密钥：
	```
	打开 git bash, 
	执行 ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
	默认保存在C:\Users\xxx\.ssh\
	```

2. 将公钥添加到 github:
	```
	复制C:\Users\xxx\.ssh\id_rsa.pub 内容
	登录github > 头像 > setting > SSH and GPG keys > New SSH key
	```

3. 编辑C:\Users\xxx\\.ssh\config:
	```
	# AAA 账户
	Host AAA
  		HostName github.com
  		User git
  		IdentityFile ~/.ssh/id_ed25519_AAA

	# BBB 账户
	Host BBB 
			HostName github.com
  		User git
  		IdentityFile ~/.ssh/id_ed25519_BBB
	```
	
4. clone 代码：
	```
	复制ssh 链接
		eg: git@github.com:userName/repository.git
	把 github.com 换成自定义的 git 账户(AAA) 
		eg: git@AAA:userName/repository.git
	```

## 2. 编辑文件 C:/Users/xxx/.gitconfig
```
	----------------------------默认配置C:/Users/xxx/.getconfig :-------
	[user]  //默认配置
		name = XXX
		email = XXX
		
	[includeIf "gitdir:X:/"]  //在 X:/下 ，用 X:/.gitconfig-AAA 的配置
			path = X:/.gitconfig-AAA
		
	[includeIf "gitdir:X:/1454/"]
			path = X:/1454/.gitconfig-BBB


	-----------------------------X:/.gitconfig-AAA :-------------------
	[user]
		name = AAA_NAME
		email = AAA_EMAIL

```