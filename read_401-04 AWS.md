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

```javascript
const dynamoose = require('dynamoose');

const peopleSchema = new dynamoose.Schema({

    'id': String,
    'name': String,
    'phone': String,

}):

module.exports = dynamoose.model('people', peopleSchema);
```

- Return to index.js
- Add:

```javascript
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




# SNS/SQS
- Amazon SNS
    - Topics - Create Topic
- SQS
    - Create Queue - Just give it a name
    - Once created, can subscribe to SNS subscriptions
    - Subscribe to the Amazon SNS topic.
- Create 2 clients with code
    - Vendor and Driver directories
    - 


# Acing the Technical Interview - Seattle JS Meetup
## Carmen, Team Hatchways - Carmen@hatchways.io
- Hatchways - a recruiting platform that does take-home assessment, similar to TripleByte
    - Less multiple-choice, more "build something"
- Before
    - Needed Background knowledge
    - Be comfortable coding on-the-spot, without using code-editor for auto-completion
    - Know the Data structures and algorithms
    - Big O notation
        - Know how to properly calculate Big O (.includes within a for loop, etc)
    - Common patterns (for efficient solutions) !!! Learn these !!!
        - Frequency counter
        - Multiple pointers
        - Sliding window
        - Divide and conquer
        - Greedy algorithm
    - Know what to expect
        - Think out loud constantly - do a lot of talking
        - Questions okay, make them infrequent and informed
        - Meaningful variable names
        - Resources:
            -  interviewing.io/recordings has actual recordings of interviews
            - interviewcake.com/interview-process-at-tech-companies
    - How to Practice
        - Focus on problem solving, not memorizing
        - Spend ~30 minutes on a problem before looking up a solution
        - Practice in one language
        - Practice consistently, short regular practice
        - Resources:
            - codingcoach.io/mock-openings
            - leetcode.com, hackerrank.com
- During
    - Approach: Option One
        - Start with discussion: ask any questions, share the game plan, explain main choice of data structure and/or algorithm
        - Solve - if you don't know immediately know the best solution, start with the simple one
        - Optimize - improve your solution and or discuss how you COULD optimize your solution
        - TEST TEST TEST - try to break your solution! If you do, thats good!
    - Approach: Option Two
        -  Understand the problem
        - ...
    - 
- Examine the question
    - Don't just jump into the problem. Even if its familiar, listen/read it VERY carefully
    - Examine the sampple input-output
- Write a template
    - Alwasy write an ACTUAL function with an ACTUAL input that handles valid inputs. Don't hardcode a solution for the sample input
- Discuss solutions
    - Don't start with the first solution that comes to your head. DISCUSS with the interviewer
    - If you know the Big O and/or think there are more efficient solutions, let the interviewer know.
    - Discussing gives the interviewer a change to help you. They may ask questions or point you to the right direction saving time.
    - If you believe your approach is not optimal, but cant think of a better one after a few minutes, go wit hthe one you have.
- Wrapping it up
    - Now you can code the solution. If you get stuck, let them know what you are thinking.
    - At some point you may figure out a more efficient solution. If almost done, finish your first solution before attempting to rewrite. Either way, inform the interviewer.
    - Once done, inspect your code to try to catch any obvious bugs and edge cases.
    - Test your function with sample input.
- What to do if stuck
    - Solve a simpler version of the question, or use an inefficient solution, even if not solving all-test cases, or solving in n^2 times
    - Walk through an example input by hand 
    - Ask these questions:
        - How would a human solve this?
        - Is there a data structure that would make this easier?
        - Would one of the problem solving pattersn help?
        - Am I using all of the information provided in the problem.
- Tips for Success
    - Don't assume a familiar looking question is one you've done before
    - Walk through edge cases examples BEFORE starting
    - Watch for signs that you might be missing something
    - Explain the ENTIRE plan before starting
    - Be EXPLICIT in your thinking of how to approach the problem as well as debugging
    - Bring up efficiency before being asked
    - Speed is SECONDARY to quality

# "What would you want to change about your role if you could?"