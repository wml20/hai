

# HIL-based Augmented ICS (HAI) Security Dataset
The HAI dataset was collected from a realistic industiral control system (ICS) testbed augmented with a Hardware-In-the-Loop (HIL) simulator that emulates steam-turbine power generation and pumped-storage hydropower generation. 

Click [here](https://github.com/icsdataset/hai/blob/master/hai_dataset_technical_details_v2.0.pdf) to find out more about HAI dataset.
> Please e-mail us [here](mailto:hkshin721@nsr.re.kr?subject=[GitHub-HAI]%20) if you have any questions about the dataset.

## Contents
- [Background](#background)
- [HAI Testbed](#hai-testbed)
- [HAI Dataset](#hai-dataset)
- [Getting the Dataset](#getting-the-dataset)
- [Performance Metric](#performance-metric)
- [Projects using the Dataset](#projects-using-the-dataset)
- [Competitions](#competitions)
- [Contributors](#contributors)
- [References](#references)


## Background

- In 2017, three laboratory-scale CPS testbeds were initially launched, namely GE’s turbine testbed, Emerson’s boiler testbed, and FESTO’s modular production system (MPS) water-treatment testbed. These testbeds were related to relatively simple processes, and were operated independently of each other.

- In 2018, a complex process system was built to combine the three systems using a hardware-in-the-loop (HIL) simulator, where thermal power generation and pumped-storage hydropower generation were simulated. This ensured that the variables were highly coupled and correlated for a richer dataset. In addition, an open platform communications united architecture (OPC-UA) gateway was installed to facilitate data collection from heterogeneous devices.

- The first version of HAI dataset, HAI 1.0,  was made available on GitHub and Kaggle in February 2020. This dataset included ICS operational data from both normal and anomalous situations for 38 attacks. Subsequently, a debugged version of HAI 1.0, namely HAI 20.07, was released for the HAICon 2020 competition in August 2020.

- HAI 21.03 was released in 2021, and is based on a more tightly coupled HIL simulator to produce clearer attack effects with additional attacks. This provided more quantitative information and covers a variety of operational situations and better insights into the dynamic changes of the physical system.

- HAI 22.04 contains more sophisticated attacks that are much more difficult to detect than previous versions. Comparing only the baseline TaPRs of HAICon 2020 and 2021, the detection difficulty is approximately four times higher than HAI 21.04.

## HAI Testbed
The testbed consists of four different processes: boiler, turbine, water-treatement and HIL simulation:

- **Boiler Process (P1):** A water-to-water heat-trasfer process with low pressure and moderate temperature. It is controlled by Emerson's Ovation DCS.
- **Turbine Process (P2):** A rotor kit process that closely simulates the behavior of an actual rotating machine. It is controlled by GE's Mark VIe DCS.
- **Water-treatment Process (P3):** A water-treatment process that includes the pumping of water to the upper reservoir and releasing it back into the lower reservoir. It is controlled by Siemens's S7-300 PLC.

- **HIL Simulation(P4):** Both of the boiler and turbine processes are interconnected to reamin sychronous with the rotating speed of the virtual steam-trubine power generation model. The pump and value in the water-treatment process are controlled by the pumped-storage hydropower generation model. The dSPACE's SCALEXIO system is used for HIL simulations and is interconnected with the real-world processes through a Siemens S7-1500 PLC and ET200 remote IO devices for data-acquisition system based on OPC gateway.


## HAI Dataset
Two major versions of HAI datasets have been released thus far. Each dataset consists of several CSV files, and each file satisfies time continuity. The quantitative summary of each version are as follows:
> **Note:** The **version numbering** follows a **date-based scheme**, where the version number indicates the released date of HAI dataset.  HAI 20.07 is the bug-fixed one of the first version HAI v1.0 released in February 2020.

<table align=center >
    <thead  align=center>
        <tr bgcolor='#bbbbbb'>
            <th rowspan=2>Version</th>
            <th rowspan=2>Data Points</th>
            <th colspan=3>Normal Dataset</th>
            <th colspan=4>Attack Dataset</th>
        </tr>
         <tr>
            <th>Files</th>
            <th>Interval</th>
            <th>Size</th>
            <th>Files</th>
            <th>Attack Count</th>
            <th>Interval</th>
            <th>size</th>
        </tr>
    </thead>
    <tbody>
          <tr bgcolor='#dddddd'>
            <td rowspan=7 align=center><b><a href="https://github.com/icsdataset/hai/tree/master/hai-22.03"> HAI 22.03<a></b> </td>
            <td rowspan=7> 78 points/sec</td>
            <td> train1.csv</td>
             <td align=right>60 hours</td>
             <td align=right>100 MB</td>
             <td> test1.csv</td>
             <td align=right>5 attacks</td>
             <td align=right>12 hours</td>
             <td align=right>22 MB</td>
          </tr>
          <tr >
             <td>train2.csv</td>
             <td align=right>63 hours</td>
             <td align=right>116 MB</td>
             <td>test2.csv</td>
             <td align=right>20 attacks</td>
             <td align=right>33 hours</td>
             <td align=right>62 MB</td>
        </tr>
        <tr bgcolor='#dddddd'>
             <td>train3.csv</td>
             <td align=right>229 hours</td>
             <td align=right>246 MB</td>
             <td>test3.csv</td>
             <td align=right>8 attacks</td>
             <td align=right>30 hours</td>
             <td align=right>56 MB</td>
        </tr>
        <tr>
             <td>train4.csv</td>
             <td align=right>229 hours</td>
             <td align=right>246 MB</td>
             <td>test4.csv</td>
             <td align=right>5 attacks</td>
             <td align=right>11 hours</td>
             <td align=right>20 MB</td>
        </tr>
        <tr bgcolor='#dddddd'> 
             <td>train5.csv</td>
             <td align=right>26 hours</td>
             <td align=right>48 MB</td>
             <td rowspan=2 colspan=4> </td>
        </tr>
        <tr>
             <td>train6.csv</td>
             <td align=right>26 hours</td>
             <td align=right>48 MB</td>
        </tr>       
        <tr >
            <td > <b>Total</b></td>
            <td align=right> <b>26 hours</b></td>
            <td align=right><b>48 MB</b></td>
            <td><b>Total</td>
             <td align=right><b>5 attacks</b></td>
             <td align=right><b>11 hours</b></td>
             <td align=right><b>20 MB</b></td>
        </tr>
        <tr bgcolor='#dddddd'>
            <td rowspan=6 align=center><b><a href="https://github.com/icsdataset/hai/tree/master/hai-21.03"> HAI 21.03<a></b> </td>
            <td rowspan=6> 78 points/sec</td>
            <td>train1.csv</td>
             <td align=right>60 hours</td>
             <td align=right>100 MB</td>
             <td> test1.csv</td>
             <td align=right>5 attacks</td>
             <td align=right>12 hours</td>
             <td align=right>22 MB</td>
        </tr>
        <tr >
             <td>train2.csv</td>
             <td align=right>63 hours</td>
             <td align=right>116 MB</td>
             <td>test2.csv</td>
             <td align=right>20 attacks</td>
             <td align=right>33 hours</td>
             <td align=right>62 MB</td>
        </tr>
        <tr bgcolor='#dddddd'>
            <td>train3.csv</td>
             <td align=right>229 hours</td>
             <td align=right>246 MB</td>
             <td>test3.csv</td>
             <td align=right>8 attacks</td>
             <td align=right>30 hours</td>
             <td align=right>56 MB</td>
        </tr>
        <tr>
            <td rowspan=2 colspan=3> </td>
             <td>test4.csv</td>
             <td align=right>5 attacks</td>
             <td align=right>11 hours</td>
             <td align=right>20 MB</td>
        </tr>
          <tr bgcolor='#dddddd'>
             <td>test5.csv</td>
             <td align=right>12 attacks</td>
             <td align=right>26 hours</td>
             <td align=right>48 MB</td>
        </tr>
        <tr >
            <td > <b>Total</b></td>
            <td align=right> <b>26 hours</b></td>
            <td align=right><b>48 MB</b></td>
            <td><b>Total</td>
             <td align=right><b>5 attacks</b></td>
             <td align=right><b>11 hours</b></td>
             <td align=right><b>20 MB</b></td>
        </tr>
        <tr >
            <td rowspan=3 align=center> <b><a href="https://github.com/icsdataset/hai/tree/master/hai-20.07"> HAI 20.07<a> </b><br> (HAI1.0)</td>
            <td rowspan=3> 59 points/sec</td>
            <td>train1.csv</td>
             <td align=right>86 hours</td>
             <td align=right>127 MB</td>
             <td>test1.csv</td>
             <td align=right>28 attacks</td>
             <td align=right>81 hours</td>
             <td align=right>119 MB</td>
        </tr>
           <tr bgcolor='#dddddd'>
            <td>train1.csv</td>
             <td align=right>91 hours</td>
             <td align=right>98 MB</td>
             <td>test1.csv</td>
             <td align=right>10 attacks</td>
             <td align=right>42 hours</td>
             <td align=right>62 MB</td>
        </tr>
           <tr >
            <td > <b>Total</b></td>
            <td align=right> <b>26 hours</b></td>
            <td align=right><b>48 MB</b></td>
            <td><b>Total</td>
             <td align=right><b>5 attacks</b></td>
             <td align=right><b>11 hours</b></td>
             <td align=right><b>20 MB</b></td>
                </tr>
    </tbody>
</table>

                
### Data fields 
                
The time-series data in each CSV file satisfies time continuity. The first column represents the observed time as “yyyy-MM-dd hh:mm:ss,” while the rest columns provide the recorded SCADA data points. The last four columns provide data labels for whether an attack occurred or not, where the attack column was applicable to all process and the other three columns were for the corresponding control processes.
> Refer to the **latest technical manual** for the details for each column.
                
<div align="center">
    
| time                  |P1_B2004        | P2_B2016| ...  | P4_HT_LD  | attack   | attack_P1   |    ...          | attack_P3 |
|:---:                  | :---:           |  :---:  |  :---: |  :---:  |  :---:   |   :---:     |  :---:         | :---:   |
|20190926 13:00:00| 0.09830         |1.07370       | ...   |  0       |  0    |   0       |    ...      | 0   |
|20190926 13:00:01| 0.09830        | 1.07410      | ...   |  0       |  1     |   0       |    ...      | 1  |
|20190926 13:00:02| 0.09830        | 1.07380        | ...   |  0       |  1     |   0       |    ...      | 1   |
|20190926 13:00:03| 0.09830        | 1.07360       | ...   |  0       |  1     |   1       |    ...      | 1   |
|20190926 13:00:04| 0.09830         | 1.07430        | ...   |  0       |  1     |  1      |    ...      | 1 |
                
</div>

## Getting the dataset
>  **NOTICE:** All data files are compressed by the standard GNU zip (gzip) due to a strict maximum size limit of 100 MB for individual files in a repository.

Type ```git clone```, and the paste the below URL. 
```
$ git clone https://github.com/icsdataset/hai
```
To unzip multiple gzip files, you can use:
```
$ gunzip *.gz
```
## Performance Metric
It is strongly recommended to use the [eTaPR (Enhanced Time-series Aware Precision and Recall)](https://github.com/saurf4ng/eTaPR) metric to evaluate your anomaly detection model, which gives fairness to performance comparisons with other studies. Got something to suggest? [Let us know!](mailto:hws23@nsr.re.kr?subject=[GitHub-eTaPR]%20)

## Projects using the dataset
Here are some projects and experiments that are using or featuring the dataset in interesting ways. Got something to add? [Let us know!](mailto:dolgam@nsr.re.kr?subject=[GitHub-HAI]%20)

The related projects so far are as follows.
### Anomaly Detection 
#### Year 2022 
1. [Benchmarking machine learning based detection of cyber attacks for critical infrastructure][AD_22_03]
2. [A Hybrid Algorithm Incorporating Vector Quantization and One-Class Support Vector Machine for industrial Anomaly Detection][AD_22_02]
3. [Variational restricted Boltzmann machines to automated anomaly detection][AD_22_01]
#### Year 2021

1. [Research on improvement of anomaly detection performance in industrial control systems][AD_21_10]
3. [E-sfd: Explainable sensor fault detection in the ics anomaly detection system][AD_21_09]
4. [Stacked-autoencoder based anomaly detection with industrial control system][AD_21_08]
5. [Improved mitigation of cyber threats in iiot for smart cities: A new-era approach and scheme][AD_21_07]
6. [Towards building intrusion detection systems for multivariate time-series data][AD_21_06]

8. [Revitalizing self-organizing map: Anomaly detection using forecasting error patterns][AD_21_04]
9. [Cluster-based deep one-class classification model for anomaly detection][AD_21_03]
10. [Measurement data intrusion detection in industrial control systems based on unsupervised learning][AD_21_02]
11. [A machine learning approach for anomaly detection in industrial control systems based on measurement data][AD_21_01]

#### Year 2020
1. [Anomaly detection in time-series data environment][AD_20_02]
2. [Detecting anomalies in time-series data using unsupervised learning and analysis on infrequent signatures][AD_20_01]

[AD_22_03]: https://ieeexplore.ieee.org/abstract/document/9687293
[AD_22_02]: https://ieeexplore.ieee.org/abstract/document/9693317
[AD_22_01]: https://link.springer.com/article/10.1007/s00521-022-07060-4

[AD_21_10]: https://link.springer.com/chapter/10.1007/978-3-030-89432-0_7
[AD_21_09]: https://ieeexplore.ieee.org/document/9568906
[AD_21_08]: https://www.scirp.org/journal/paperinformation.aspx?paperid=106463
[AD_21_07]: https://www.mdpi.com/1424-8220/21/6/1976
[AD_21_06]: https://link.springer.com/chapter/10.1007/978-3-030-96057-5_4

[AD_21_04]: https://link.springer.com/chapter/10.1007/978-3-030-78120-0_25
[AD_21_03]: https://jit.ndhu.edu.tw/article/view/2553
[AD_21_02]: https://www.aimspress.com/article/doi/10.3934/aci.2021004
[AD_21_01]: https://www.mdpi.com/2079-9292/10/4/407
[AD_20_02]: https://dl.acm.org/doi/abs/10.1145/3440943.3444353
[AD_20_01]: https://www.koreascience.or.kr/article/JAKO202009252091939.page


### Testbed/Dataset 
#### Year 2021 
1. [Probabilistic attack sequence generation and execution based on mitre att&ck for ics datasets][TB_21_01]

#### Year 2020
1. [Expansion of ICS testbed for security validation based on MITRE ATT&CK techniques][TB_20_01] 
2. [Expanding a programmable cps testbed for network attack analysis][TB_20_02]
3. [Co-occurrence based security event analysis and visualization for cyber physical systems][TB_20_03]

[TB_21_01]: https://dl.acm.org/doi/abs/10.1145/3474718.3474722 "CSET 2021"  
[TB_20_01]: https://www.usenix.org/conference/cset20/presentation/choi "CSET 2020"
[TB_20_02]: https://dl.acm.org/doi/abs/10.1145/3320269.3405447 "Asis CCS 2020"
[TB_20_03]: https://link.springer.com/chapter/10.1007/978-3-030-50732-9_70 "HCI 2020"
         
                
## Competitions 
Since 2020, we have held two AI competitions using the HAI dataset. The competition website shares the competition baseline codes and winner's codes.
 * HAICon 2020 (HAI 22.04): https://dacon.io/competitions/official/235624/overview/description
 * HAICon 2021 (HAI 21.03): https://dacon.io/en/competitions/official/235757/overview/description
        
                
## Contributors
Hyeok-Ki Shin, Woomyo Lee, Jeong-Han Yun, and Byung-Gil Min in the Affiliated Institute of ETRI, Daejeon, South Korea.
                
## License
This work is licensed under a [Creative Commons Attribution-ShareAlike License (CC BY-SA 4.0)](http://creativecommons.org/licenses/by-sa/4.0/).

## Citation
1. Won-Seok Hwang, Jeong-Han Yun, Jonguk Kim and HyoungChun Kim, "[Do You Know Existing Accuracy Metrics Overrate Time-Series Anomaly Detection?][5]", In the 37th ACM/SIGAPP Symposium On Applied Computing (SAC 2022), 2022.
2. Hyeok-Ki Shin, Woomyo Lee, Jeong-Han Yun, and HyoungChun Kim, "[Two ICS Security Datasets and Anomaly Detection Contest on the HIL-based Augmented ICS Testbed][4]", In the 14th  Cyber Security Experimentation and Test (CSET '21), Pages 36–40, 2021.
3. Hyeok-Ki Shin, Woomyo Lee, Jeong-Han Yun, and HyoungChun Kim, "[HAI 1.0: HIL-based Augmented ICS Security Dataset][3]", In the 13th USENIX Workshop on Cyber Security Experimentation and Test (CSET '20), Santa Clara, CA, 2020.
4. Won-Seok Hwang, Jeong-Han Yun, Jonguk Kim and HyoungChun Kim, "[Time-Series Aware Precision and Recall for Anomaly Detection: Considering Variety of Detection Result and Addressing Ambiguous Labeling][2]", CIKM '19:Proceedings of the 28th ACM International Conference on Information and Knowledge Management, pp.2241-2244, 2019.
5. Seungoh Choi, Jeong-Han Yun, Sin-Kyu Kim, "[A Comparison of ICS Datasets for Security Research Based on Attack Paths][1]", In: Luiijf E., Žutautaitė I., Hämmerli B. (eds) Critical Information Infrastructures Security. CRITIS 2018. Lecture Notes in Computer Science, vol 11260. Springer, Cham.
                
[5]: http://www.sigapp.org/sac/sac2022/program.html "SAC 2022"
[4]: https://dl.acm.org/doi/abs/10.1145/3474718.3474719 "CSET '21"
[3]: https://dl.acm.org/doi/abs/10.5555/3485754.3485755 "CSET '20"
[2]: https://dl.acm.org/doi/10.1145/3357384.3358118 "CIKM '19"
[1]: https://link.springer.com/chapter/10.1007/978-3-030-05849-4_12 "CRITIS 2018"
                
## Dataset Metadata
The following table is necessary for this dataset to be indexed by search
engines such as <a href="https://g.co/datasetsearch">Google Dataset Search</a>.
<div itemscope itemtype="http://schema.org/Dataset">
<table>
  <tr>
    <th>property</th>
    <th>value</th>
  </tr>
  <tr>
    <td>name</td>
    <td><code itemprop="name">HIL-based Augmented ICS Security Dataset</code></td>
  </tr>
  <tr>
    <td>alternateName</td>
    <td><code itemprop="alternateName">HAI Security Dataset</code></td>
  </tr>
  <tr>
    <td>alternateName</td>
    <td><code itemprop="alternateName">hai seucrity dataset</code></td>
  </tr>
  <tr>
    <td>url</td>
    <td><code itemprop="url">https://github.com/icsdataset/hai</code></td>
  </tr>
  <tr>
    <td>sameAs</td>
    <td><code itemprop="sameAs">https://github.com/icsdataset/hai</code></td>
  </tr>
  <tr>
    <td>description</td>
    <td><code itemprop="description">The HAI security dataset was collected from a realistic Industiral Control System (ICS) testbed augmented with a Hardware-In-the-Loop (HIL) simulator that emulates steam-turbine power generation and pumped-storage hydropower generation. 
 </code></td>
  </tr>
  <tr>
    <td>provider</td>
    <td>
      <div itemscope itemtype="http://schema.org/Organization" itemprop="provider">
        <table>
          <tr>
            <th>property</th>
            <th>value</th>
          </tr>
          <tr>
            <td>name</td>
            <td><code itemprop="name">The Affiliated Institute of ETRI, South Korea</code></td>
          </tr>
          <tr>
            <td>sameAs</td>
            <td><code itemprop="sameAs">https://github.com/icsdataset</code></td>
          </tr>
        </table>
      </div>
    </td>
  </tr>
  <tr>
    <td>license</td>
    <td>
      <div itemscope itemtype="http://schema.org/CreativeWork" itemprop="license">
        <table>
          <tr>
            <th>property</th>
            <th>value</th>
          </tr>
          <tr>
            <td>name</td>
            <td><code itemprop="name">CC BY 4.0</code></td>
          </tr>
          <tr>
            <td>url</td>
            <td><code itemprop="url">https://creativecommons.org/licenses/by/4.0/</code></td>
          </tr>
        </table>
      </div>
    </td>
  </tr>
   <tr>
    <td>citation</td>
        <td>
       <code itemprop="citation">https://dl.acm.org/doi/abs/10.1145/3474718.3474719</code>
       <code itemprop="citation">https://dl.acm.org/doi/abs/10.5555/3485754.3485755</code>
       <code itemprop="citation">https://dl.acm.org/doi/10.1145/3357384.3358118</code>
       </td>
  </tr>
</table>
</div>
