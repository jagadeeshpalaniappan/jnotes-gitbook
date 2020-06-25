# Overview

{% tabs %}
{% tab title="12 Factor Apps" %}
* Kubernetes is best suitable for `12 Factor Apps`

1. TODO
2. TODO
3. .....
{% endtab %}

{% tab title="Docker" %}


* **Dockerfile** &gt;&gt; **Docker Image** \(hosted in dockerhub registry\)  &gt;&gt; **Containers**

![](../../.gitbook/assets/image%20%2814%29.png)
{% endtab %}

{% tab title="Docker vs VM" %}
In VM, Guest OS takes lot of resources \(RAM, CPU,…\)  // We don’t need Guest OS in Containers

![](../../.gitbook/assets/image%20%2828%29.png)
{% endtab %}
{% endtabs %}

\*\*\*\*

### Kubernetes: Overview

{% tabs %}
{% tab title="Orchestration" %}


![](../../.gitbook/assets/image%20%2819%29.png)
{% endtab %}

{% tab title="Kubernetes Architecture" %}


![](../../.gitbook/assets/image%20%2820%29.png)
{% endtab %}

{% tab title="" %}

{% endtab %}
{% endtabs %}

\*\*\*\*

### Kubernetes: Key Topics:

{% tabs %}
{% tab title="NameSpaces" %}


![](../../.gitbook/assets/image%20%2822%29.png)
{% endtab %}

{% tab title="Contexts" %}


![](../../.gitbook/assets/image%20%2830%29.png)
{% endtab %}

{% tab title="Pods" %}


![](../../.gitbook/assets/image%20%289%29.png)
{% endtab %}

{% tab title="Volume" %}
![](../../.gitbook/assets/image%20%2815%29.png)

**Persistent Volumes**

![](../../.gitbook/assets/image%20%2816%29.png)
{% endtab %}

{% tab title="Services" %}


![](../../.gitbook/assets/image%20%2811%29.png)
{% endtab %}

{% tab title="Deployments" %}


![](../../.gitbook/assets/image%20%2823%29.png)
{% endtab %}

{% tab title="Deployments - Rollouts and Rollbacks" %}


![](../../.gitbook/assets/image%20%2827%29.png)
{% endtab %}

{% tab title="ReplicaSets" %}

{% endtab %}

{% tab title="External Access" %}

{% endtab %}

{% tab title="Ingress" %}
External Access

![](../../.gitbook/assets/image%20%2813%29.png)

**Ingress**

![](../../.gitbook/assets/image%20%288%29.png)

![](../../.gitbook/assets/image%20%2826%29.png)
{% endtab %}
{% endtabs %}

### Kubernetes: Other Topics:

{% tabs %}
{% tab title="ConfigMaps" %}
![](../../.gitbook/assets/image%20%2810%29.png)
{% endtab %}

{% tab title="Secrets" %}
![](../../.gitbook/assets/image%20%2829%29.png)
{% endtab %}

{% tab title="Security Contexts" %}
![](../../.gitbook/assets/image%20%2824%29.png)
{% endtab %}

{% tab title="Network Policies" %}
![](../../.gitbook/assets/image%20%2817%29.png)
{% endtab %}

{% tab title="Labels & Selectors" %}
![](../../.gitbook/assets/image%20%2812%29.png)
{% endtab %}

{% tab title="Annotations" %}
![](../../.gitbook/assets/image%20%2821%29.png)
{% endtab %}

{% tab title="Liveness and Readiness Probes" %}
![](../../.gitbook/assets/image%20%2818%29.png)
{% endtab %}

{% tab title="Resource Quotas" %}
![](../../.gitbook/assets/image%20%2825%29.png)
{% endtab %}

{% tab title="" %}

{% endtab %}
{% endtabs %}

\*\*\*\*

{% tabs %}
{% tab title="High Level Summary" %}
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
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}



