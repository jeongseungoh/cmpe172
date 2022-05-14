# spring-gumball ci/cd example


## CI Workflow

For the examination, we need to pull the spring-gumball from the professor's repository (Lab 10) into the personal GitHub Repo as public.
   https://github.com/paulnguyen/cmpe172/tree/main/labs/lab10/spring-gumball
   
![Picture3](https://user-images.githubusercontent.com/75586376/168411286-cebd0b66-be90-410e-9f1c-256debdd92d9.jpg)

After creating the repository into the personal Repo, we set up the building tool to Gradle and JDK 11. (https://github.com/jeongseungoh/spring-gumball)
![Picture1](https://user-images.githubusercontent.com/75586376/168411275-530c6fb1-6b6f-4921-b287-8ad22b625998.jpg)

Then, we create the "main.yml" file which controls the CI of JAVA with Gradle into the workflows.
![Picture4](https://user-images.githubusercontent.com/75586376/168411325-81235c6b-3201-41b2-8b35-0ec5184bede5.jpg)

When we finish to save the file and click the action in the GitHub, we can see the Java CI is working to build.
![Picture5](https://user-images.githubusercontent.com/75586376/168411401-99d5996b-63c4-4bd4-8c3b-5b0231dce8f6.jpg)

If there is no errors, the CI file is successfully working.


## CD Workflow

Foe CD workflow exercise, we need to set up the GKE as below picture:
![Picture6](https://user-images.githubusercontent.com/75586376/168411473-5907e35c-ff8d-4a18-96ef-f3934b9e1dd8.jpg)

And then, we create the kubernetes cluster.
![Picture9](https://user-images.githubusercontent.com/75586376/168411496-3a0ea68d-764e-4f5a-8ed6-75592761fa4c.jpg)

When we finish generating the kubernate cluster, we create a key in the service account. Then, we create the setting the GKE_PROJECT and GKE_SA_KEYS in the GitHub.
![Picture7](https://user-images.githubusercontent.com/75586376/168411872-1d1ffd25-f6df-4432-ac64-96170a47021f.jpg)
![Picture8](https://user-images.githubusercontent.com/75586376/168411933-f3b67655-accc-4492-9fd0-6dcc37fc413c.jpg)

Before generating the gke.yml file for the CD workflow, we need to check the parts (GKE_CLUSTER, GKE_ZONE, DEPLOYMENT_NAME) in the yml.
![Picture10](https://user-images.githubusercontent.com/75586376/168412567-18dcb65a-6a48-445c-a909-7be0dc538aec.jpg)

When we  are done with above steps, we release the workflows.
![Picture11](https://user-images.githubusercontent.com/75586376/168412774-ec2b7194-fa83-49e8-96aa-5263911e28e2.jpg)

I got the error at the first release.
![Picture12](https://user-images.githubusercontent.com/75586376/168412853-d6ef4f2c-b4b1-480d-9e92-17dc8af81eee.jpg)

For fixing the error, I added the role in the service account. When I added that, the "get-gke-credentials" part was fixed.
![Picture13](https://user-images.githubusercontent.com/75586376/168412925-78222cb0-d34b-4726-82a2-bea6ab47a67b.jpg)

However, the other error was popped out.
![Picture14](https://user-images.githubusercontent.com/75586376/168412966-62bd9962-34c1-4358-8102-7db2265be379.jpg)

For fixing the 'storage.bucket.create' permission, I added the other role (Storage Admin) into the service account.
![Picture15](https://user-images.githubusercontent.com/75586376/168413025-9b02519a-0f2a-4332-a385-acdf3fddee2a.jpg)

When I finished all things, I could successfully release the "spring-gumball" Repo.
![Picture16](https://user-images.githubusercontent.com/75586376/168413082-25a487da-0f46-4c29-9c16-0c911f402a1c.jpg)

If the process is successful, the delpoyment and service are generated in the cluster.
![Picture17](https://user-images.githubusercontent.com/75586376/168413124-6d22ddfd-7305-4490-a5c8-9284a7963750.jpg)
![Picture18](https://user-images.githubusercontent.com/75586376/168413126-cc61a62c-e95b-4236-a2d9-80aab2418387.jpg)
![Picture19](https://user-images.githubusercontent.com/75586376/168413128-8834301d-6991-47f2-88eb-f0493a827d9b.jpg)

For the Load Balancer of the gumball program, we need to set up the cookies in the load balnacer section of the cluster.
![Picture19](https://user-images.githubusercontent.com/75586376/168413157-35de1b9d-b796-479c-9d0c-e94635993a86.jpg)
![Picture20](https://user-images.githubusercontent.com/75586376/168413159-2a1066b4-28fe-4b05-b8d9-598c03cb36f5.jpg)
![Picture22](https://user-images.githubusercontent.com/75586376/168413161-ae899dab-22ce-488e-ae85-04147db2db81.jpg)
![Picture21](https://user-images.githubusercontent.com/75586376/168413160-77edbf2d-1398-4b91-81ed-803f87ac3661.jpg)

Finally, we can see the gumball page when we click the frontend address.
![Picture23](https://user-images.githubusercontent.com/75586376/168413185-ec52d3cf-0867-4ffa-bcd1-f30f6991eb95.jpg)


[full screenshot of the desktop]
![Picture24](https://user-images.githubusercontent.com/75586376/168413191-049c64ff-3cd8-44c4-a7e9-a316c47358c5.jpg)
