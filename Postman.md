# Postman/wireshark/tcpdump/git/nmap

# Postman Object (read swagger.io/ openAPI)
* pm.request
* pm.response
* pm.globals
* pm.collectionVariables
* pm.environment
* pm.variable 

# sample
dans le Test: 

json style
```
let token = pm.response.json().access_token
pm.global.set('token',token)
```
or 
regex style
```
let token = responseBody.match('"access_token:"(.*?)"')
pm.global.set('token',token[1])

order of reading by Postman.
pm.collectionVariables.set()
pm.environment.set()
pm.global.set()

# Automation with expect
pm.test("success post request", function(){
    pm.expect(pm.response.code.to.be.oneOf([200,201]);
});
pm.test("body string", function(){
    pm.expect(pm.response.text()).to.include("size");
});
pm.test("status code is 200", funciton(){
    pm.response.to.have.status(200);
})
pm.test("response timeout", function(){
    pm.expect(pm.reponse.responseTime).to.be.below(200);
})


pm.sendRequest('http://192.168.1.1:8080/static/postman.js',(err,res) =>{
    eval(res.text());
    beifan_assert(
        200,{
            "id: 1,
            "title": "null".
            "is_done": "false"
        },
        pm.globals.get('old_title')
    );
});
```