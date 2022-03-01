# containerlab
Experiment with real-time network telemetry using [containerlab](https://containerlab.srlinux.dev/) to simulate Clos (leaf/spine) fabrics.

[Real-time telemetry from a 5 stage Clos fabric](https://blog.sflow.com/2022/02/real-time-telemetry-from-5-stage-clos.html)

[Topology aware fabric analytics](https://blog.sflow.com/2022/02/topology-aware-fabric-analytics.html)

## 5 Stage Clos Topology
![](clos5.png)

Deploy 5 stage Clos topology:

`containerlab deploy -t clos5.yml`

Generate traffic between `h1` and `h4`:

`docker exec -it clab-clos5-h1 iperf3 -c 172.16.4.2`

Connect to http://localhost:8008/ for analytics, see [Quickstart](https://sflow-rt.com/intro.php) for more information.

## 3 Stage Clos Topology
![](clos3.png)

Deploy 3 stage Clos topology:

`containerlab deploy -t clos3.yml`

Generate traffic between `h1` and `h2`:

`docker exec -it clab-clos3-h1 iperf3 -c 172.16.2.2`

Connect to http://localhost:8008/ for analytics, see [Quickstart](https://sflow-rt.com/intro.php) for more information.

# EVPN Topology
<img src="evpn3.png" width="600">

Deploy EVPN topology:

`containerlab deploy -t evpn3.yml`

Generate traffic between `h1` and `h2`:

`docker exec -it clab-evpn3-h1 iperf3 -c 172.16.10.2`

Connect to http://localhost:8008/ for analytics, see [Quickstart](https://sflow-rt.com/intro.php) for more information.

# DDoS Topology
![](ddos.png)

Deploy DDOS topology:

`containerlab deploy -t ddos.yml`

Simulate DDoS attack against `victim`:

`docker exec -it clab-ddos-attacker hping3 --flood --udp -k -a 198.51.100.1 -s 53 192.0.2.129`

Connect to http://localhost:8008/ for analytics, see [Quickstart](https://sflow-rt.com/intro.php) for more information.
