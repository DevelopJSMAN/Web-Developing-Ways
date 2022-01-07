# Web-Developing-Ways
 Basical 3 Ways of the Web Developing
 1. Static Contents : Display the file as it is in a web browser.
 2. MVC(Model-View-Control) and Template Engine : By programming with template engine like JSP, PHP,,, and it makes the page dynamic.
 3. API : Delivering the data to Clients with Data-Structure-Format like json,,,

<How it works, Static Cotents?>

I made a simple html code like 'Hello, 안녕하세요!!'. 

Explaning with it, There are Web Browser, Internal Tomcat Server, Spring Boot and Spring Container.

First, Typing 'localhost:8080/hello' on Web Browser's search box, the Internal Tomcat server receives the request.
And the Internal Tomcat server gives  the request first to Spring Container of Spring Boot. Because the Spring Container has the priority. If there is not Controller named 'hello', it finds 'hello' resource in the resources folder and display as it is in the Web Browser.

<How about MVC and Template Engine?>
 
 MVC : Model, View, Controller
 
For studying MVC, I made a new Controller in HelloController with @GetMapping
 <img width="667" alt="스크린샷 2022-01-07 오후 3 24 10" src="https://user-images.githubusercontent.com/86109402/148503012-f1e918c9-a2ac-4e4d-96d1-597ce3b4e6ee.png">
 
And made a template named 'hello-template.html' and pasted the html codes.
<img width="439" alt="스크린샷 2022-01-07 오후 3 23 51" src="https://user-images.githubusercontent.com/86109402/148503229-e89c84a1-17c1-4354-9491-ce3b8bb59e5e.png">

**In 3th line, 'hello! empty' is actually not neccessary, but it is the benefit of thymeleaf.
  Because it shows the previous contents by just looking the codes in advance.

Typing 'localhost:8080/hello-mvc' on the search box in the Web Browser.
 <img width="658" alt="스크린샷 2022-01-07 오후 3 25 12" src="https://user-images.githubusercontent.com/86109402/148503662-e1b62c55-683b-41d1-ac20-2a2b52adea62.png">
 
I found it doesn't work! Why?
<img width="1223" alt="스크린샷 2022-01-07 오후 3 25 51" src="https://user-images.githubusercontent.com/86109402/148503894-f4b854f5-0509-45c5-8c4a-e83819c36d94.png">
<img width="1227" alt="스크린샷 2022-01-07 오후 3 28 22" src="https://user-images.githubusercontent.com/86109402/148503906-90b715e0-5590-4d1e-9972-04919c8c2f49.png">

 
There is a warning sentence that required request parameter 'name' for method parameter type String is not present.
So I add some words after the sentence i wrote to 'localhost:8080/hello-mvc?name=spring!
 <img width="1118" alt="스크린샷 2022-01-07 오후 3 32 03" src="https://user-images.githubusercontent.com/86109402/148504321-ee0b7e47-1b3a-4065-8a90-6178216dd8c1.png">

**It doesn't matter to type anything you want on the 'spring!' of '?name=spring!'

MVC and Template's Engine is something different from static content's engine.
The Internal Tomcat server receives the request.
And the Internal Tomcat server gives  the request to Spring Container - helloController, it returns hello-template modeling 'name:spring' to viewResolver.
viewResolver requests Thymeleaf template engine to find the same hello-template, then template engine works and translating to HTML, returns results to Web Browser.

<API>
 
There is no viewResolver in API, so it is neccessary to add the @ResponseBody.
And API returns not letter but object.
 
<img width="160" alt="스크린샷 2022-01-07 오후 4 38 55" src="https://user-images.githubusercontent.com/86109402/148509058-b918daf5-8c62-43b2-b3ac-59e3eebdd3f5.png">

It shows comparing to other ways. Because it uses JSON.
It consists the structure of {[key] : [value]}
 
How is it constructed?
 
 <img width="559" alt="스크린샷 2022-01-07 오후 4 33 22" src="https://user-images.githubusercontent.com/86109402/148509491-b745b0aa-b758-4a13-9fd0-7360adfe35b1.png">

 Because of declaring with private, so when i want to use this String, use this Methods named 'Getter and Setter'.
 
API engine is?
 The Internal Tomcat server receives the request, and the Internal Tomcat server gives the request to Spring Container - helloController.
 But there is the annotation called @ResponseBody. and returning objects to HttpMessageConverter.
 So HttpMessageConverter works instead of viewResolver.
 
 ** Default Letter proccessing : 'StringHttpMessageConverter'
 ** Default Object Proccessing : 'MappingJackson2HttpMessageConverter'
