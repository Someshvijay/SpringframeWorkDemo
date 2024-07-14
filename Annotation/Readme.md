##Annotation based 

###Main.java

```java
package org.someshspringrameworkDemo;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;
public class Main {
    public static void main(String[] args) {

        ApplicationContext context = new ClassPathXmlApplicationContext("spring.xml");

        Staff staff = context.getBean(Nurse.class);
        staff.assist();

    }
}
```

###Doctor.java

```java
package org.someshspringrameworkDemo;
import org.springframework.stereotype.Component;

@Component
public class Doctor implements Staff {

    public void assist(){
        System.out.println("Doctor is assisting");
    }

}
```


###Nurse.java

```java
package org.someshspringrameworkDemo;
import org.springframework.stereotype.Component;

@Component
public class Nurse implements Staff{
    public void assist(){
        System.out.println("Nurse is assisting");
    }
}
```



###spring.xml

```xml
<?xml version="1.0" encoding="UTF-8" ?>

<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context" xsi:schemaLocation="
        http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">


<context:component-scan base-package="org.someshspringrameworkDemo"></context:component-scan>


<!-- bean definitions here -->
<!--    <bean id="doctor" class="org.someshspringrameworkDemo.Doctor">-->
<!--        <constructor-arg value="MBBS"></constructor-arg>-->

<!--    </bean>-->
<!--    <bean id="nurse" class="org.someshspringrameworkDemo.Nurse"></bean>-->



</beans>
```
