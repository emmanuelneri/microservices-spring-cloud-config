# microservices-spring-cloud-config

Configurações do Spring Cloud Config Server do projeto https://github.com/emmanuelneri/microservices-spring-cloud

## Hierarquia dos arquivos de configurações

É utilizado o recurso de configurações default do Spring Boot, onde as configurações como o nome application automaticamente são herdadas por outras configurações mais específicas, dessa forma todos herdam as propriedades de application.properties e todos *-dev.properties herdam de application-dev.properties e todos *-docker.properties herdam de application-docker.properties. Dessa forma, os arquivos de configurações são mais reaproveitados entre as aplicações.

![alt tag](https://github.com/emmanuelneri/microservices-spring-cloud-config/blob/master/others/hierarquia.png)

#### Exemplo:

A aplicação receiver rodando com o profile de dev, o endereço requisitado é http://localhost:8888/receiver/dev no config server e o retorno é o json abaixo:
```
{  
   "name":"receiver",
   "profiles":[  
      "dev"
   ],
   "label":null,
   "version":"c83b4168add7ffcb5fc62be3709a7557a6b84f9a",
   "state":null,
   "propertySources":[  
      {  
         "name":"https://github.com/emmanuelneri/microservices-spring-cloud-config/receiver-dev.properties",
         "source":{  
            "spring.rabbitmq.host":"localhost"
         }
      },
      {  
         "name":"https://github.com/emmanuelneri/microservices-spring-cloud-config/application-dev.properties",
         "source":{  
            "eureka.instance.hostname":"localhost"
         }
      },
      {  
         "name":"https://github.com/emmanuelneri/microservices-spring-cloud-config/receiver.properties",
         "source":{  
            "server.port":"8090",
            "queue.order.name":"OrderQueue"
         }
      },
      {  
         "name":"https://github.com/emmanuelneri/microservices-spring-cloud-config/application.properties",
         "source":{  
            "info.app.name":"@project.artifactId@",
            "info.app.version":"@project.version@"
         }
      }
   ]
}
```
