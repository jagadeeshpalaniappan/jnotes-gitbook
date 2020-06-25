# Overview



* Kubernetes works better for `12 Factor App`
* Dockerfile &gt;&gt; Docker Image \(hosted in dockerhub registry\)  &gt;&gt; Container![](cid:68BF2DEC-D9E0-405A-AE58-40987109A1E1@hsd1.ca.comcast.net)  
* In VM, Guest OS takes lot of resources \(RAM, CPU,…\) 
  * * We don’t need Guest OS in Containers
* 
![](cid:68BF2DEC-D9E0-405A-AE58-40987109A1E1@hsd1.ca.comcast.net)

![](cid:4134D521-521C-4778-992B-F3E728B964B0@hsd1.ca.comcast.net)  
  
**Kubernetes Architecture:**  
![](cid:31E419C3-5E2D-457E-9259-60CBDA83CDFF@hsd1.ca.comcast.net)  
  
  
**AWS Cluster1**

* **Context1**
  * **NameSpace1**
    * deployment1
      * replicaset1
        * pod1
          * **service1** \(ClusterIP\) // access within cluster
          * **service2** \(NodePort\)  // access outside cluster
          * **service3** \(LoadBalancer\) //..
          * ---
          * container1
          * container2
          * ...
        * pod2
      * replicaset2
        * pod1
        * pod2
    * deployment2
  * **NameSpace2**
* **Context2**
  * pod1
    * **service1** \(ClusterIP\) // access within cluster
    * **service2** \(NodePort\)  // access outside cluster
    * **service3** \(LoadBalancer\) //...
  * pod2

  
  
  
**Contexts:  \(Cluster\)**  
![](cid:C24BA3D5-FBAB-4F08-9C71-A6D783C72308@hsd1.ca.comcast.net)  
**Namespaces:**  
![](cid:97C76F03-FA03-4177-BE3D-671A880282B7@hsd1.ca.comcast.net)  
  
  
**Deployment:**![](cid:77F335EF-583B-4701-BD5C-F610CD5F8E30@hsd1.ca.comcast.net)  
  
**Services:**![](cid:B4114AD2-2168-4DB5-B08C-22456BA4C0FA@hsd1.ca.comcast.net)  
  
  
  


