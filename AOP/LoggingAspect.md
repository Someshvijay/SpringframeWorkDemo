# Logging Aspect Example


### Main.java
```java
package org.somesh_spring_aop;

import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;

public class Main {
    public static void main(String[] args) {
        ApplicationContext context = new AnnotationConfigApplicationContext(BeanConfig.class);

        ShoppingCart shoppingCart = context.getBean(ShoppingCart.class);
        shoppingCart.checkout("Cancelled");
    }
}
```

### BeanConfig.java
```java
package org.somesh_spring_aop;

import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.EnableAspectJAutoProxy;

@Configuration
@ComponentScan(basePackages = "org.somesh_spring_aop")
@EnableAspectJAutoProxy
public class BeanConfig {
}
```

### ShoppingCart.java
```java
package org.somesh_spring_aop;

import org.springframework.stereotype.Component;

@Component
public class ShoppingCart {

    public void checkout(String status){

        //Logging
        //Authentication and authorization
        //Sanitize the data
        System.out.println("Checkout method from shoppingCart called");
    }
}
```

### LoggingAspect
```java
package org.somesh_spring_aop;

import org.aspectj.lang.annotation.After;
import org.aspectj.lang.annotation.Aspect;
import org.aspectj.lang.annotation.Before;
import org.springframework.stereotype.Component;

@Aspect
@Component
public class LoggingAspect {

    //This is an example of logging
    // and tells us how to run these , where these methods would be called before and after checkout() method

    //.checkout(..) - the 2 dot will match whatever parameters are there in the component
    @Before("execution(* org.somesh_spring_aop.ShoppingCart.checkout(..))")
    public void beforeLogger(){
        System.out.println("Before Loggers");
    }

    // After - This line equates to "for any return type, for any package, any class if there is a checkout method"
    @After("execution(* *..*.checkout(..))")
    public void afterLogger(){
        System.out.println("After Logger");
    }
}
```
