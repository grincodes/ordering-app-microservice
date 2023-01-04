nest generate app -- converts project to a monorepo

npm run start:dev app-name ; eg npm run start:dev billing

nest g library common ; create a place to put common code used
by different apps 

Mongodb replica set from bitnami allows db transactions 

consider having seperate package.jsin across apps instead of sharing one
in this case we are sharing one 

@InjectConnection() - passing connection for transaction sake 

docker compose up --build -V

app.get() ; gets any injectable instance

- npm i @nestjs/microservices

# Hybrid Microservice
An hybrid application listens for both http request as well as 
make use of conneceted microservice.
he INestApplication instance can be connected with INestMicroservice instances through the connectMicroservice() method.

```const app = await NestFactory.create(AppModule);
const microservice = app.connectMicroservice({
  transport: Transport.TCP,
});

await app.startAllMicroservices();
await app.listen(3001);```

The normal way to create a microservice is to use nest factiry .createMicroservice Method
```
const app = await NestFactory.create(AppModule);
const microservice = app.connectMicroservice({
  transport: Transport.TCP,
});

await app.startAllMicroservices();
await app.listen(3001);
```

RabbitMq based microservice

Dynmamic Module 


# steps to exchange Msg in microservice
 -  register the service in your module using the clientModule
 - inject the service as a clientProxy

   app.useGlobalPipes(new ValidationPipe()); allows you to make use of class validator

# Eks Deployment

   use helm

   Helm is a package manager for kuberneets
   Helm sends config to TILLER which needs to be installed on your kubernetes


Docker build - before pushing to docker hub

cmd
``` - docker build ../../ -f Dockerfile -t designerseyi12345
/
ordering-app_billing ```

docker image push designerseyi12345/ordering-app_orders

keep secrets put of kuberneted deployment file
put them in secrets 

Installing with helm
helm install ordering-app .

Configure kubernetes on your docker desktop (Make sure its running)
artifacthub.io - is used to implement dependencies like rabbitmq and mongodb on helm chart

use helm values to override dependency config properties

cmd - helm uninstall ordering-app
cmd- helm dependency update // install dependencies

kubectl get svc
use the headless service to connect to pods

helm upgrade ordering-app . 
kubectl logs 
kubectl expose deployment auth --type='NodePort' --port=3001