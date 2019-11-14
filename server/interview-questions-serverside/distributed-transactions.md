# Distributed Transactions

## Data Consistency

### Data Consistency Problems in Microservice & How 'Saga' helps

{% tabs %}



{% embed url="https://www.youtube.com/watch?v=YPbGW3Fnmbc" caption="" %}

### Business Criteria

![](../../.gitbook/assets/image-200.png)

![](../../.gitbook/assets/image-147.png)

![](../../.gitbook/assets/image-68.png)

![](../../.gitbook/assets/image-100.png)

But

![](../../.gitbook/assets/image-36.png)

### Microservice

![](../../.gitbook/assets/image-164.png)

![](../../.gitbook/assets/image-73.png)

![](../../.gitbook/assets/image-28.png)

### Microservice DataConsistency

![](../../.gitbook/assets/image-51.png)

![](../../.gitbook/assets/image-189.png)

![](../../.gitbook/assets/image-118.png)

![](../../.gitbook/assets/image-212.png)

![](../../.gitbook/assets/image-55.png)

![](../../.gitbook/assets/image-213.png)

![](../../.gitbook/assets/image-43.png)

![](../../.gitbook/assets/image-113.png)

![](../../.gitbook/assets/image-195.png)

![](../../.gitbook/assets/image-75.png)

![](../../.gitbook/assets/image-152.png)

![](../../.gitbook/assets/image-173.png)

![](../../.gitbook/assets/image-60.png)

![](../../.gitbook/assets/image-32.png)

![](../../.gitbook/assets/image-179.png)

![](../../.gitbook/assets/image-59.png)

![](../../.gitbook/assets/image-9.png)

![](../../.gitbook/assets/image-48.png)

#### Recommended Solutions:

![](../../.gitbook/assets/image-132.png)

![](../../.gitbook/assets/image-64.png)

![](../../.gitbook/assets/image-166.png)

![](../../.gitbook/assets/image-123.png)

![](../../.gitbook/assets/image-104.png)

![](../../.gitbook/assets/image-112.png)

![](../../.gitbook/assets/image-7.png)

![](../../.gitbook/assets/image-95.png)

![](../../.gitbook/assets/image-120.png)

![](../../.gitbook/assets/image-105.png)

![](../../.gitbook/assets/image-93.png)

![](../../.gitbook/assets/image-125.png)

### 1. Use 'Table' & `Keep Polling the Table` -to Publish the Msg

![](../../.gitbook/assets/image-39.png)

![](../../.gitbook/assets/image-81.png)

### 2. Use 'Table' & `Tail DB Logs` --to Publish the Msg

![](../../.gitbook/assets/image-53.png)

![](../../.gitbook/assets/image-46.png)

### Data Consistency Problems \(more..\)

{% tabs %}
{% tab title="2" %}
![](../../.gitbook/assets/image-136.png)

![](../../.gitbook/assets/image-176.png)

![](../../.gitbook/assets/image-38.png)
{% endtab %}

{% tab title="3" %}
![](../../.gitbook/assets/image-161.png)

![](../../.gitbook/assets/image-129.png)

![](../../.gitbook/assets/image-199.png)
{% endtab %}

{% tab title="4" %}
![](../../.gitbook/assets/image-67.png)

![](../../.gitbook/assets/image-89.png)
{% endtab %}

{% tab title="5" %}
![](../../.gitbook/assets/image-72.png)
{% endtab %}

{% tab title="6" %}
![](../../.gitbook/assets/image-66.png)
{% endtab %}

{% tab title="7" %}
![](../../.gitbook/assets/image-23.png)

Not everywhere we need Data Consistency

For example, \(Here we may have Data Inconsistency

1. In online shopping website
   1. Sometimes you see, Data Inconsistency
   2. For example, In search page, **Item shows Available**
   3. But actually if you click that **Item details** and see it shows **"Not Available"**
2. ![](../../.gitbook/assets/image-24.png)
{% endtab %}

{% tab title="8" %}
![](../../.gitbook/assets/image-45.png)
{% endtab %}

{% tab title="9" %}
![](../../.gitbook/assets/image-211.png)
{% endtab %}
{% endtabs %}

## Kafka

### What is Kafka

{% tabs %}

![](../../.gitbook/assets/image-159.png)

![](../../.gitbook/assets/image-54.png)

ss

![](../../.gitbook/assets/image-20.png)

![](../../.gitbook/assets/image-153.png)

![](../../.gitbook/assets/image-121.png)

![](../../.gitbook/assets/image-180.png)

![](../../.gitbook/assets/image-128.png)

![](../../.gitbook/assets/image-69.png)

![](../../.gitbook/assets/image-184.png)

![](../../.gitbook/assets/image-145.png)

![](../../.gitbook/assets/image-94.png)

![](../../.gitbook/assets/image-63.png)

![](../../.gitbook/assets/image-193.png)

![](../../.gitbook/assets/image-177.png)

![](../../.gitbook/assets/image-188.png)

![](../../.gitbook/assets/image-192.png)

![](../../.gitbook/assets/image-186.png)

![](../../.gitbook/assets/image-187.png)

![](../../.gitbook/assets/image-97.png)

![](../../.gitbook/assets/image-77.png)

![](../../.gitbook/assets/image-207.png)

![](../../.gitbook/assets/image-35.png)

![](../../.gitbook/assets/image-12.png)

![](../../.gitbook/assets/image-190.png)

![](../../.gitbook/assets/image-156.png)

![](../../.gitbook/assets/image-31.png)

![](../../.gitbook/assets/image-168.png)

![](../../.gitbook/assets/image-210.png)

![](../../.gitbook/assets/image-182.png)

![](../../.gitbook/assets/image-76.png)

![](../../.gitbook/assets/image-115.png)

![](../../.gitbook/assets/image-140.png)

![](../../.gitbook/assets/image-102.png)

![](../../.gitbook/assets/image-138.png)

![](../../.gitbook/assets/image-83.png)



{% embed url="https://www.youtube.com/watch?v=I32hmY4diFY" caption="" %}

### Why Kafka

{% tabs %}

![](../../.gitbook/assets/image-3.png)

![](../../.gitbook/assets/image-197.png)

![](../../.gitbook/assets/image-58.png)

