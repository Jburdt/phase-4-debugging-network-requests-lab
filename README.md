# Putting it All Together: Client-Server Communication

## Learning Goals

- Understand how to communicate between client and server using fetch, and how
  the server will process the request based on the URL, HTTP verb, and request
  body
- Debug common problems that occur as part of the request-response cycle

## Introduction

Just like the last lesson, we've got code for a React frontend and Rails API
backend set up. This time though, it's up to you to use your debugging skills to
find and fix the errors!

To get the backend set up, run:

```console
$ bundle install
$ rails db:migrate db:seed
$ rails s
```

Then, in a new terminal, run the frontend:

```console
$ npm install --prefix client
$ npm start --prefix client
```

Confirm both applications are up and running by visiting
[`localhost:4000`](http://localhost:4000) and viewing the list of toys in your
React application.

## Deliverables

In this application, we have the following features:

- Display a list of all the toys
- Add a new toy when the toy form is submitted
- Update the number of likes for a toy
- Donate a toy to Goodwill (and delete it from our database)

The code is in place for all these features on our frontend, but there are some
problems with our API! We're able to display all the toys, but the other three
features are broken.

Use your debugging tools to find and fix these issues.

There are no tests for this lesson, so you'll need to do your debugging in the
browser and using the Rails server logs and `byebug`.

**Note**: You shouldn't need to modify any of the React code to get the
application working. You should only need to change the code for the Rails API.

As you work on debugging these issues, use the space in this README file to take
notes about your debugging process. Being a strong debugger is all about
developing a process, and it's helpful to document your steps as part of
developing your own process.

## Your Notes Here

- Add a new toy when the toy form is submitted

  - How I debugged:

  I looked at the dev tools. The console said a server 500 error. So I went and looked at the last request I sent through. If you read it it says what line the erros is on. I changed Toys.create to Toy.create.

- Update the number of likes for a toy

  - How I debugged:

  Clicked the like button. Looked at my dev tools to see an error about unexpected end of JSON. Looked at the fetch nethod then made sure my controller action was good. I put a debugger in first to look at the params. then I looked at the rest of the controller and added render json: toy

- Donate a toy to Goodwill (and delete it from our database)

  - How I debugged:
  
  Clicked the donate button. Looked at my Dev tools to see a 500 error. Looks at my rails server logs to see I didn't have a destroy action in my routes. Added destroy to routes.