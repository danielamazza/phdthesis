---
date: 2017-05-21T18:42:19+02:00
title: Chapter 2 - A Partial Computation Offloading Technique
---
## 2.1 Introduction

Smart cities are considered a paradigm where wireless communication is an enhancing factor to make better urban services and improve the quality of life for citizens and visitors. In a smart city scenario several entities should be taken into consideration: the wireless infrastructure that allows data-exchange, the user devices, the sensing nodes, the machine devices, access points, one or more cloud infrastructures. Moreover, for delivering the requested services lots of data are exchanged among the citizens and the devices, and these data need also to be elaborated in order to give the correct information to the users. Thanks to various wireless communication technologies, users can move through different environments, indoor and outdoor, providing data to the cloud and receiving access services as browsing, video on demand, video streaming, information about location and maps. In this context, energy saving and performance improvement of the SMDs have been widely recognized as primary issues. In fact, the execution of every complex application is a big challenge due to the limited battery power and computation capacity of the mobile devices, especially in a smart environment where communication is considered a key to get better features in important areas such as mobility and transportation.

The exploitation of HetNet infrastructures together with the opportunity to delegate computation load to MCC, as shown in fig. 2.1, is an appealing connection achieving the aims of saving the SMD's power resource and executing the requested tasks in a faster way [23].

{{< figure src="../../figures/HetNet_MCC.PNG" title="Fig 2.1 - The reference scenario with access nodes in HetNet for Mobile Cloud Computing." >}}


HetNets involve multiple types of low power radio access nodes in addition to the traditional macrocell nodes in a wireless network, reaching the major goal to enhance connectivity. On the other hand, MCC aims to increase the computing capabilities of mobile devices, to conserve local resources - especially battery charge - to extend storage capacity and to enhance data safety for making the computing experience of mobile users better [25] .

The distributed execution (i.e., computation/code offloading) between the cloud and mobile devices has been widely investigated [9], highlighting the challenges towards a more efficient cloud-based offloading framework and also suggesting some opportunities that may be exploited. Indeed, the joint optimization of HetNets and distributed processing is a promising research trend [5] .

Several works have already analyzed characteristics and capacity of MCC offloading, for example aiming to extract offloading friendly parts of codes from existing applications [26], [27]. Also, in [28] the key issues are identified when developing new applications which can effectively leverage cloud resources. Furthermore, in [29] a real-life scenarios, where each device is associated to a software clone on the cloud, has been considered, and in [30] a system that effectively accounts for the power usage of all of the primary hardware subsystems on the phone has been implemented, distinguishing between CPU, display, graphics, GPS, audio, and microphone.

In [31] an offloading framework, named Ternary Decision Maker (TDM), has been developed, aiming to shorten response time and reduce energy consumption simultaneously with targets of execution including on-board CPU and GPU in addition to the cloud, from the point of view of the single device. In addition, there are many studies that focus on whether to offload computation to a server, providing solutions related to a yes/no decision for the entire task at one time [32], [33] or studies that focus on optimization of the energy consumption in SMDs necessary to run a given application under execution time constraint [34].

Differently from the literature, we propose a partial offloading technique able to exploit the HetNets scenario and the presence of MCC devices - the UMCC framework - by optimizing the amount of partial offloading of the computational tasks depending on the number of devices connected to a network and their location with respect to the WiFi access points or LTE eNodeBs. The SMDs can exploit the partial data offloading to distribute high computational tasks among centralized servers and local computing.

In Fig. 2.2 the workflow and the entities involved in the performance of a task are shown. From the point of view of a single user, the decision about offloading or not is taken on the basis of the following considerations:

* If the task is delegated to the cloud, the energy consumed by the mobile device is due to the data transfer - uploading data and downloading results - plus the energy consumed in an idle state during the outside computation - waiting for the results; the global time for having the task accomplished is related not only to the computational time but also to the transfer time for moving data from the mobile device to the cloud and vice-versa.

* If the task is computed locally, the energy consumed by the mobile device is due to the computation itself; the global time for having the task accomplished is related only to the computational ability of the SMD.

{{< figure src="../../figures/offloadingOrNot.jpg" title="Fig 2.2 - The offloading decision from the point of view of a single user." >}}

In this chapter the optimization of the entire system is considered, not for a single device but for the whole community of devices, by taking into account partial offloading in a non trivial multi-objective optimization approach, where both energy consumption and execution time constraints are considered. A cost function including the tradeoff between energy consumption of mobile devices versus the time to offloading data and to compute tasks on a remote cloud server is provided, evaluating the optimal offloading fraction depending on the network's load. It can be exploited when the network is overloaded and the tasks request large amounts both of computation to perform and data to exchange.

## 2.2 System Model

The reference scenario is characterized by a urban area with a pervasive wireless coverage, where several mobile devices are interacting with a traditional centralized cloud and request for services from a remote data center, as illustrated in Fig. 2.1. Alongside the presence of a pervasive wireless network, the system deals with many sensing and user terminals that generate and exploit a large amount of data. In order to connect the SMDs to the cloud and the data centers for delegating data for the computation, we take into account a simple categorization of the UMCC's trasmission entities, considering only two types of RATs forming the basic elements of the HetNets: macrocells and small cells. If, on one side, the strategy of delegating computation to the centralized cloud allows to exploit high performance computing centers, on the other side, it copes with the energy spent by the SMDs for transferring data. Similarly, the SMDs which compute locally the applications in a distributed approach, face with the energy issues due to the computation itself. In other words, the SMDs consumes energy both to delegate the application to the data centers and to compute it locally. Furthermore, both the speed to transmit data and the speed for local computation are related to the energy consumed by the SMDs. Thus, the offloading decision between offloading the application or computing it locally leads to a tradeoff. For this reason our model provides a cost function by resorting to a previously introduced model in [32], [33] which compares the energy used for a 100\% offloading with the ones used to perform the task locally. The parameters used in the following are listed in tab 2.1.

symbol	meaning	unit of measure
P
l
Pl	power for local computing	W
P
id
Pid	power while being idle	W
P
tr
Ptr	power for sending and receiving data	W
S
md
Smd	SMD’s calculation speed	no. of instructions / s
S
tr
Str	SMD’s transmission speed	bit / s
S
cs
Scs	cloud server’s calculation speed	no. of instructions / s
C
C	instructions required by the task	no. of instructions
D
D	exchanged data	bit Table 2.1: Offloading Parameters 

In our scenario we suppose that the computation of a certain task requires 
C
C instructions. 
S
md
Smd and 
S
cs
Scs are, respectively, the speeds in instructions per second of the mobile device and the cloud server. Hence, a certain task can be completed in an amount of time equal to 
C
/
S
md
C/Smd on the device and 
C
/
S
cs
C/Scs on the server. On the other hand, let us suppose that 
D
D corresponds to the amount of bits of data that the device and the server must exchange for the remote computation, and 
S
tr
Str is the transmission speed, in bit per second between the SMD and the access point; hence, the transmission of data lasts an amount of time equal to 
D
/
S
tr
D/Str. In this case we consider that the transmission time is mostly due to the access network transfer, because the transfer rate of the backbone network can be considered as negligible due to the higher data rate. Moreover, we consider as negligible the transfer time from the access point to the user terminal because the amount of data in response to the elaboration in centralized server is little with respect to the data sent to the centralized server [32], [33].

Hence, it is possible to derive the energy for local computing:

 E
l
=
P
l
×
C
S
md
  
(2.1)
 
(2.1)El=Pl×CSmd
as the product of the power consumption of the mobile device for computing locally, 
P
l
Pl, and the time 
C
/
S
md
C/Smd needed for the computation. Similarly, it is possible to derive the energy needed for performing the task computation on the cloud as the energy used while being in idle for the remote computation plus the energy used to transmit the whole data from the SMD to the cloud:

 E
od
=
P
id
×
C
S
cs
+
P
tr
×
D
S
tr
,
  
(2.2)
 
(2.2)Eod=Pid×CScs+Ptr×DStr,
where 
P
id
Pid and 
P
tr
Ptr are the power consumptions of the mobile device, in watts, during idle and data transmission periods, respectively.

Similarly, it is possible to derive the time needed for the local computing as:

 T
l
=
C
S
md
  
(2.3)
 
(2.3)Tl=CSmd
and the time for the whole offloading computing as

 T
od
=
C
S
cs
+
D
S
tr
  
(2.4)
 
(2.4)Tod=CScs+DStr
In many applications, this approach is not efficient or feasible, and it is necessary to partition the application at a finer granularity into local and remote parts, which is a key step for offloading.

Adaptive Offloading

In this section, firstly, two equations are provided, to represent the energy used by a SMD to execute an application in partial offloading and to express the time needed to execute such application. Secondly, the impact of the traffic workload in the wireless network is taken into account, since the RATs and the number of SMDs entails the transmission speed of the the offloading data. Thirdly, a cost function is introduced, to evaluate the percentage of offloading which minimizes both energy and time.

In order to analyze the energy spent for offloading only a part of the application, we introduce the weight coefficients 
γ
γ and 
δ
δ, satisfying 
0
≤
γ
,
δ
≤
1
0≤γ,δ≤1, representing respectively the percentage of the computational task and the percentage of the exchanged data for offloading. Then, the used energy of a single device 
E
part
_
od
Epart_od has been introduced, as the sum of the one spent to perform a part of the task locally plus the one spent to idle and transmit the other part of the task to the cloud:

 E
part
_
od
=
P
l
×
(
1
−
γ
)
⋅
C
S
md
+
P
id
×
γ
⋅
C
S
cs
+
P
tr
×
δ
⋅
D
S
tr
  
(2.5)
 
(2.5)Epart_od=Pl×(1−γ)⋅CSmd+Pid×γ⋅CScs+Ptr×δ⋅DStr
Taking into account the same coefficients 
γ
γ and 
δ
δ used in eq. 
2.5
2.5, we can calculate the time for the partial offloading 
T
part
_
od
Tpart_od as the maximum between the time needed for computing the local part of the task and the time needed for the offloading, considering the two phases performed in the same time:

 T
part
_
od
=
max
(
(
1
−
γ
)
⋅
C
S
md
;
γ
⋅
C
S
cs
+
δ
⋅
D
S
tr
)
  
(2.6)
 
(2.6)Tpart_od=max((1−γ)⋅CSmd;γ⋅CScs+δ⋅DStr)
The structure and the workload of the network are implicitly considered in eqs. 
2.5
2.5 and 
2.6
2.6. Now we are going to describe the effect on 
E
part
_
od
Epart_od and 
T
part
_
od
Tpart_od due to the different RATs performing in the HetNets and to the amount of devices connected to this different RATs. The HetNet mainly consists of two components, macrocells and small cells, with different bandwidths 
BW
BW. Since, for a single SMD, the speed rate of the data exchange 
S
tr
Str is affected by the bandwidth of the node to which the SMD is connected, by the distance 
d
d from this node, and by the number 
n
n of the overall SMDs connected to the same node, 
S
t
r
Str can be written in an explicit way as:

 S
t
r
=
BW
n
⋅
log
2
(
1
+
SNR
d
2
)
  
(2.7)
 
(2.7)Str=BWn⋅log2⁡(1+SNRd2)
where 
SNR
SNR is the SNR, typical parameter of the device.

In order to allow the evaluation of the offloading percentage, aiming to save energy and improve performance, the introduction of a cost function that can consider the minimization of both eqs. 
2.5
2.5 and 
2.6
2.6 for the entire set of SMDs is required. This is a non-trivial multi-objective optimization problem that we addressed by setting the cost function as a weighted sum of both the average values, with 
α
α and 
β
β coefficients with the constraints 
0
≤
α
,
β
≤
1
0≤α,β≤1 and 
α
+
β
=
1
α+β=1, 
N
N number of network's devices and 
E
l
El, 
T
l
Tl reference values representing average energy and time spent when the task is computed locally by a SMD:

 F
=
α
1
N
∑
N
k
=
1
E
part
_
od
,
k
(
γ
,
δ
)
E
l
+
β
1
N
∑
N
k
=
1
T
part
_
od
,
k
(
γ
,
δ
)
T
l
  
(2.8)
 
(2.8)F=α1N∑k=1NEpart_od,k(γ,δ)El+β1N∑k=1NTpart_od,k(γ,δ)Tl
This cost function is based on a network centric approach in which a central entity is responsible for choosing values of the offloading percentage 
γ
γ and 
δ
δ after collecting informations about the SMDs' features. Furthermore, in the partial offloading procedure, 
γ
γ and 
δ
δ are bounds, because before a task is executed it may require certain amount of data from other tasks [23]. Moreover, the weighted coefficients 
α
α and 
β
β are chosen at a main level to give a major importance to energy or time saving.

Numerical Results

During a partial offloading the amount of energy and time in eqs. 
2.5
2.5 and 
2.6
2.6 is affected by the percentage of computation and communication exchanged, represented respectively by the coefficients 
γ
γ and 
δ
δ. These are correlated each other, since the execution of a remote computation task requires a certain amount of input/output data to be exchanged. So we can consider the ratio 
δ
/
γ
δ/γ as a typical value, peculiar of a type of application. To summarize typical scenarios we have taken into account three kinds of applications represented in Table 2.2, according to the aims to analyze cases of a smart transportation system [35]

Application	Computation	Data Transmission	C	D	
δ
/
γ
δ/γ
1 - Real time traffic analysis	High	Low	
10
7
107	
10
5
105	
0.25
0.25
2 - Mobile video and audio communication	Low	High	
10
5
105	
10
7
107	
0.75
0.75
3 - Mobile Social Networking	High	High	
10
7
107	
10
7
107	
0.50
0.50 Table 2.2: Application Types 

We considered a deployment area of 
1000
×
1000
 
m
2
1000×1000 m2, where one LTE eNodeB with channel capacity equal to 100 MHz and three WiFi access point with channel capacities equal to 22 MHz are positioned to cover the entire area. Specifically, the access points are positioned at point (0,0), (500,1000) and (0,1000), and the LTE station at (500,500), as shown in fig. 2.3.

Fig 2.3 - Area in case of 500 and 5000 SMD connected, where the access points are positioned at point (0,0), (500,1000) and (0,1000), and the LTE station at (500,500).

The values of 
S
md
Smd, 
P
id
Pid, 
P
tr
Ptr and 
P
l
Pl are specific parameters of the mobile device. For example we utilized the values of an HP iPAQ PDA with a 400 MHz Intel XScale processor (
S
md
=
400
Smd=400) and the following values: 
P
l
≈
0.9
W
Pl≈0.9W, 
P
id
≈
0.3
W
Pid≈0.3W and 
P
tr
≈
1.3
W
Ptr≈1.3W [32].
The cost function coefficients, 
α
α and 
β
β, are equal to 0.5, aiming to give the same importance to both time and energy consumptions. In Figures 2.4, 2.5, and 2.6 the performance results of the cost function are represented for the three applications described in tab 2.2.

Fig. 2.4 shows that, when a task requires high computation and low communication, i.e. Application 1, it is better to offload the task totally, no matter how many devices are connected to the network. In fact, the curves are overlapped and the cost function assumes the sames values for the same percentage 
γ
γ.

On the other hands, Fig. 2.5 shows that, when a task requires low computation and high communication, i.e. Application 2, it is better to compute the task locally. In this case a big number of connected devices affects the cost function in a negative way; it is possible to see that there is a minimum for 
γ
γ = 0.

The most interesting case is shown in Fig. 2.6. In fact, when the network is overloaded, tasks with both a large amount of computation to execute and data to exchange - as in Application 3 - are better performed for a specific value of 
γ
γ. For example, in this case, the best performance is for 
γ
=
0.4
γ=0.4 when a population of 5000 devices is whithin the area, and 
γ
=
0.7
γ=0.7 for a population of 2000 devices. When the network is not overloaded, instead, as in cases of less devices within the area, it's better to perform the total offloading.

Fig 2.4 - Cost function behavior for Application 1 - Real Time Traffic Analysis.

Fig 2.5 - Cost function behavior for Application 2 - Mobile Video and Audio Communication.

Fig 2.6 - Cost function behavior for Application 3 - Mobile Social Networking.

Finally, as shown in \autoref{fig:enApp3adapt} and \autoref{fig:timeApp3adapt}, we compare energy and time spent in the adaptive case with those spent for the local execution and the total offloading case to perform Application 3; for the adaptive algorithm we have considered the use of the optimized 
γ
γ parameter following the previous analysis. While for the energy there is a compromise between the two boundary cases, the adaptive function allows the best performance considering time as the primary issue.

Fig 2.7 - Energy for Application 3 - Mobile Social Networking.

Fig 2.8 - Time for Application 3 - Mobile Social Networking.

Conclusions

In this chapter, a cost function has been defined for optimizing contemporaneously time and energy consumption in a scenario where smart mobile devices are supposed to perform an application; the aim was to optimize the amount of computation performed locally and remotely. The remote execution is faster and can relieve mobile devices from the correlated energy consumption, but it involves data exchange with the cloud server, spending time and energy to transmit, depending also from the load of the HetNet. The cost function is proposed to evaluate the percentage of application to offload for time and energy optimization. The results show that for applications requesting both high execution work and data exchange a particular value of this percentage, depending on the number of devices, optimize the performance.