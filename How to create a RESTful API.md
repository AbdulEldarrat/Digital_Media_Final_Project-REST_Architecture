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
