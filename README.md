# Process_Mining_synthetic_data-creation
Synthetic data generation using Python package [Faker](https://faker.readthedocs.io/en/master/), event-log generation with Python and initial analysis using Open-Source-Tool [ProM](https://promtools.org/). <br>

#### Tools:
* [Jupyter Notebook](https://jupyter.org/)
* [ProM](https://promtools.org/)

***
These first steps and analyses with process mining were done in the context of a master thesis. To learn more about process mining and the initiation, implementation and development of process mining, the thesis ***Optimizing the Initiation of Process Mining Projects:** A strategic approach to increase maturity* can be read. <br>
In order to choose a suitable method to carry out the process mining project, the [**IID-Framework**](master_thesis_IID-Framework/thesis_artefact_IID-framework.xlsx) developed in the master thesis was used. Due to the lack of experience in process mining, the **Process Diagnostics Method** (PDM) of Boskaya et al. is choosen. <br>
All files related to the IID-Framework can be found in the [master_thesis_IID-Framework](master_thesis_IID-Framework) folder.
***

### Problem:
During the implementation of a process mining project in a manufacturing German company, it was unfortunately not possible to obtain real process data.

### Solution: 
To solve the problem and to gain first experiences with process mining, synthetic data was generated. Data of a logistic process should be created.
The article [*'Process Mining in 5 Schritten'*](https://www.informatik-aktuell.de/betrieb/kuenstliche-intelligenz/process-mining-in-5-schritten.html) was used as an example to generate the logistics data.<br>

***
## Procedure:
1. Creating three data sources. These are combined into one data table based on their foreign key relationships. The following code is used for this: [Faker_data_generator.ipynb](Faker_data_generator.ipynb) <br>

   *The data sources come from three different systems:*
      1. **Warehouse-Management-System:** Movements in the WMS &rarr; **Result:** [synthetic_WMS_data.csv](created_files/datatables/synthetic_WMS_data.csv)
      2. **Picking-System:** Picking information &rarr; **Result:** [synthetic_VER_data.csv](created_files/datatables/synthetic_VER_data.csv)
      3. **Shipping-System:** Shipping information &rarr; **Result:** [synthetic_KOM_data.csv](created_files/datatables/synthetic_KOM_data.csv)
      4. **Merged data source:** Including all information from 1, 2 & 3 &rarr; **Result:** [synthetic_merged_data.csv](created_files/datatables/synthetic_merged_data.csv)
      
2. Using the [synthetic_merged_data.csv](synthetic_merged_data.csv) as input for [event-log_creator.ipynb](event-log_creator.ipynb), to create a Event-log. An Event-log was created which uses all information from the available data sets. Furthermore, an edited event log was created, which only contains entries for further use. <br>
   1. **Event-log:** Contains all informations from the provided datasets &rarr; **Result:** [event-log.csv](created_files/event-logs/event-log.csv)
   2. **Short Event-log:** Contains only time-related informations &rarr; **Result:** [event-log_short.csv](created_files/event-logs/event-log_short.csv)
  
3. Using **ProM-tool** for analysis
   1. Create an XES-file with the *Convert CSV to XES*-Plugin <br>
      ![ProM Overview - CSV parser](/images/ProM_csv_parser.PNG "ProM Overview - CSV parser")
   3. A Process flow was created with the *Heuristic Miner* <br>
      ![Process Flow_Heuristic Miner](/images/process_flow_HeuristicMiner_ProM.jpg "Process Flow mined with the Heuristic Miner")
   4. Perform a Control flow analysis to find out the *Precision and Fitness* of the process model on the event log <br>
      ![Precision and Fitness](/images/precision_and_fitness_ProM.jpg "Precision and Fitness process model to Event-log")
   5. Make a Performance analysis for time-related *Performance Evaluations* <br>
      ![Average sojourn time](/images/time_performance_evaluations_ProM.jpg "Average sojourn time per activity")

## Useful links:
* Faker documentation: [here](https://faker.readthedocs.io/en/master/)
* ProM tool: [here](https://promtools.org/)
* IID-Framework: [here](/master_thesis_IID-Framework)

***
### Author:
Florian Obersteiner

