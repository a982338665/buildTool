


**1.���ܣ�**

    let secret = datiConfig.jwtTokenSecret;
    let expires = moment().add('days', 7).valueOf();
    //����token
    let token = jwt.encode({
        iss: user.user_code,
        exp: expires
    }, secret);


**2.���ܣ�**

    let secret = datiConfig.jwtTokenSecret;
    var decoded = jwt.decode(token, secret);
    if (decoded.exp <= Date.now()) {
        res.sendStatus(401);
        return;
    }
    
**3.���ã�**

    var datiConfig = {
        jwtTokenSecret: 'xxxxx'
    }
