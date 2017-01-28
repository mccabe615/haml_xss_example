# ToDo application

##### Login

User: test@test.com
Password: password

Application is vulnerable to XSS on the main page with the following URL:
http://127.0.0.1:3000/?%22%3E%3Cscript%3Ealert(1)%3C/script%3E=1

Example of proper encoding:
http://127.0.0.1:3000/?id=%3Cscript%3Ealert(1)%3C/script%3E

Vulnerable code:

```
    .row-fluid
      .span10.offset1
        .hero-unit.text-center
          %h1
            ToDo
          %input{:type=>"hidden", :data=>params, :id=>"current_tab"}  
          %p
            %a{href: 'http://www.arubystory.com', target: '_blank'}
              Welcome to the ToDo application
          .text-center
```

Code from:

http://www.arubystory.com/2013/12/tutorial-creating-simple-todo.html
