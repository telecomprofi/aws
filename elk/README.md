##Deploy ELK in AWS with Ansible##

##Veryfied on `Ubuntu 16.04 LTS`

**1.Add your aws SSH private key to the ssh-agent for access to the aws hosts.**

```bash
ssh-add elk.pem
```

**2. Verify that python is installed on the aws hosts.**

```bash
python --version
```
If python isn't installed you should install it.

```bash
sudo apt install python-minimal
```

**3.Create inventory file for playbook.**

```bash
vi hosts
```

```bash
[aws_1] 
hostname1 aws_2=hostname2

[aws_2]
hostname2
```

aws_1 host for Kibana and Logstash 
aws_2 host for Elasticsearch


**4.Modify logstash `input.conf` and `filter.conf` with your input and filter settings if needed**

If you didn't configure logstash input and filter config you can load test data(after installing elk) for checking that elk stack works correct using following link:

* https://www.elastic.co/guide/en/kibana/current/tutorial-load-dataset.html

**5.Install elk to the aws with ansible.**

```bash
ansible-playbook elk.yml -i hosts
```



Links:
* https://www.elastic.co/