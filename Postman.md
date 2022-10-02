# Postman/wireshark/tcpdump/git/nmap

# Postman learning Center

* [https://learning.postman.com/docs/getting-started/introduction/ ](https://learning.postman.com/docs/getting-started/introduction/)

* install newman - CLI which less secure for safe environement: [https://learning.postman.com/docs/running-collections/using-newman-cli/installing-running-newman/](https://learning.postman.com/docs/running-collections/using-newman-cli/installing-running-newman/)



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
            "access_token": "string", // test if token is string
            "token_type": "string"
        },
        "bearer"
    );
});
```

# Real example
 * sign in to get token
 * create task to get task_id
 * based on task_id , modify task, get, delete. 
 * based on task_id, confirmed that task has been deleted.

step by step
 - create collection : takeaway
 - create variable: under takeaway, go to variables, create variable [base_url, token, todo_id]
 - add request
 - associated connector
 - expect
 - job batch
