
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

let token = pm.response.json().access_token
pm.global.set('token',token)

or 
regex style

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
