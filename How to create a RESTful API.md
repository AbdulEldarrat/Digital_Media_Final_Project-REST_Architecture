## How to create a RESTful API?
#### In this tutorial we will be going over the basics of how to create a simple, yet effective RESTful API using java. This can be done in any IDE which supports java.
#### However, in this tutorial we will be using Spring, and the Spring IDE.

*First* - We create a Greeting class which will model the greeting object we will send to the endpoint

    package hello;

    public class Greeting {

        private final long id;
        private final String content;

        public Greeting(long id, String content) {
            this.id = id;
            this.content = content;
        }

        public long getId() {
            return id;
        }

        public String getContent() {
            return content;
        }
    }

*Next* - We need to create the application class which will startup the application, this class is usually autocreated in the Spring IDE, however, if you are developing in another IDE you will need to create this yourself

package hello;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;


    @SpringBootApplication
    public class Application {

        public static void main(String[] args) {
            SpringApplication.run(Application.class, args);
        }
    }
    
*Lastly* - We need to create a controller class which will be the endpoint for our communication

    package hello;

import java.util.concurrent.atomic.AtomicLong;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

    @RestController
    public class GreetingController {

        private static final String template = "Hello, %s!";
        private final AtomicLong counter = new AtomicLong();

        @RequestMapping("/greeting")
        public Greeting greeting(@RequestParam(value="name", defaultValue="World") String name) {
            return new Greeting(counter.incrementAndGet(),
                                String.format(template, name));
        }
    }
    

And thats it! you now have a RESTful api which will accept HTTP `GET` requests at 
   `http://localhost:8080/greeting1`
   
And the response will be a greeting in JSON that will look like this
    `{"id":1,"content":"Hello, World!"}`
