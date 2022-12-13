# http-https

    const t = require('http_and_https');
    const fs = require('fs');

    
    const httpServer = t.http.createServer((req, res)=>{
        res.writeHead(301,{Location: `https://${req.headers.host}${req.url}`});
        res.end();
    }).listen(80);

    const httpsServer = t.https.createServer({key: fs.readFileSync('key.pem'),cert: fs.readFileSync('cert.pem')},(req, res)=>{
        res.writeHead(200);
        res.end("hello world\n");
    }).listen(443);