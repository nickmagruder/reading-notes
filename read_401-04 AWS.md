# Wednesday 

# Integrating AWS Services
- 10:25
- API: https://us-east-2.console.aws.amazon.com/apigateway/main/apis?region=us-east-2
        - Creating a REST API in
    - Create new API 
    - NEW API
        - Endpoint type: Regional (not CDN)
    -Resources
        - What endpoint/methods?
        -Actions - add resources
        - Name: people
        - Path: /people
    - Create a method - Define an HTTP method for accessing resource
    - Define GET on /people
        - /people GET Setup
            - Integration type: Lambda Function
                - Must have a function set-up in the region selected (since doing endpoint Regional)
    - Create the  Lambda Function 
    - 10:35
        - node.js 14.x runtime
        - name "read-people"
    - Return to defining GET on /people
        - Lambda function: read-people
        - Select "use lambda proxy integration" YES
        - Add permission to Lambda Function - OK
        - We now have a testable route - 3-10 1.png
            - TEST, displays the AWS response object log
            - Don't add trigger yet
    - Deploying
    - 10:44
        - Actions
            - Deploymenty stage new stage
            - name : test
            - description "testing state for API routes"
        - Creates a URL (that won't do anything at this point, no actions)
    - Finding an error after deploying
        - Go to CloudWatch - Log Groups

- DynamoDB
    - NoSQL AWS DB
    - Create DynamnoDB Table
    - 10:48
        - name:
        - primary key: id, string !!!!!
            - "Scaler values"
            - Make sure you know what data type your primary key is going to be
            - Whatever we choose we will have to make happen in the lambda function
        - Use Default settings
        - Create.
        - When created, values can be added from GUI
            - Overview gives basic overview
        - Creating an item: 
        - 10:52
            - id: 001
            - + insert: string: name: Jacob
            - If saving without unique ID it will error
        - We do want a schema
        - It is now possible to fetch from this DB
- Fetching 
- 10:56
    - Return to Function's "code source" "3-10 2.png"
- Dynamoose 
    - Basic overview at:
    - 10:58-11:01
    - Dynamo DB Api structured like Mongoose
    - Dynamoose runs primary off of roles
- Making a package.json for Dynamoosing
- 11:11
    - mkdir readpeople
    - create an index.js

        ```
        exports.handler = async (event)=> {
            let response = {
                statusCode: 200,
                body: 'test'
            }
            return response
        }
        ```

- See Dynamoose documentation 
- Dynamoose Will look for AWS "environment variables" (see documantation section)
- IAM Role section in docs !!!
- Add permision? 
- 11:16
    - not needed
    - Instead go to "role"
    - Atach policies
        - search: dynamo
        - Attach Policy: AmazonDynamoDBFullAccess
            - Attach directly to role associated with Lambda
            - See "Lambda Handlers" seciton in lecture notes
- Back to directory readpeople
- Create people.schema.js
```
const dynamoose = require('dynamoose');

const peopleSchema = new dynamoose.Schema({

    'id': String,
    'name': String,
    'phone': String,

}):

moduke.exports = dynamoose.model('people', peopleSchema);
```

- Return to index.js
- Add:

```
const peopleModel = requre('./people.schema.js'):
```


        ```javascript
        exports.handler = async (event)=> {

            let data;

            try {
                data = await peopleModel.scan().exec();

            } catch (e) {

                **SEE DEMO FOR CODE**
            }


            let response = {
                statusCode: 200,
                body: JSON.stringify(data),
            }
            return response;
        }
        ```

- Return to terminal
- zip -r function.zip .
    - zips this directory
- Return to Lambda Function GUI
- 11:30
    - Upload the zip in readpeople
    - Check logs because it will be broken
    - Fix, rezip, re-upload

- GET function 
- 11:37
- Line 7 on index.js demo code - 11:41
    - Ninja code?

- POST 
- 11:47
    - Select resource (route) that you watn to append to
    - Add a method of post
    - Integration type: Lambda
    - Need whole new Lambda
    - Return to Lambda
    - Create new function
        - return to method and select the Lambda
        - Make another directory
        - index.js
        - Dynamoose
        - Copypasta from the other index.js and schema
        - Do 50 other things and then maybe it will work.
- Lab Overview 
- 12:02

