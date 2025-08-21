# sign up
1. 客户端 https 传输  明文密码
2. 服务端 保存加密密码
    ```
    import bcrypt from 'bcrypt'
    let encrypt-pswd = await bcrypt.hash(pswd,  12)
    ```

# login
1. 客户端 https 传输  明文密码
2. 服务端 校验
    ```
    import bcrypt from 'bcrypt'
    let encrypt-pswd = query from db
    let isValid = await bcrypt.compare(pswd,  encrypt-pswd)
    ```
2. 服务端 生成 token
    ```
    import jwt from 'jsonwebtoken'
    let token = jwt.sign({name,  id, ...}, ENV_JWT_SECRET, { expiresIn: '1h' })
    let isValid = await bcrypt.compare(pswd,  encrypt-pswd)
    ```
# API verify
1. 客户端携带 token： ` request.headers.Authorization = 'Bearer ' + token`
2. 服务端 校验 token
   ```
   import jwt from 'jsonwebtoken'
   let author = jwt.verify(token, ENV_JWT_SECRET)
   ```

