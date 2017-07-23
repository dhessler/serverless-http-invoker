# serverless-http-invoker
Locally invoke [Serverless](https://github.com/serverless/serverless) functions via their HTTP event as specified in Serverless.yml. 

It makes it easy to test not only your handler logic, but also ensures that you have your http events setup properly in serverless.yml without deploying.


# Usage
Use it in tests of Serverless functions to test your HTTP endpoints along with the handler code. For example, you can write the following to test a Serverless function:

    it('should invoke simple path', function () {
      let response = invoker.invoke('GET api/hello')  
      return expect(response).to.eventually.have.property('statusCode', 200)
    })

The test above is a test of a Serverless function defined in Serverless.yml as follows:

    functions:
      hello:
        handler: handler.hello
        events:
          - http:
              path: api/hello
              method: get


# Installation
npm (`npm install serverless-http-invoker --save-dev`) or yarn (`yarn add serverless-http-invoker --dev`)