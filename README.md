# 🚀 UiPath Dispatcher – ACME System 1 (Work Item 4)  

## 📌 Description  
This project implements the **Dispatcher** part of the REFramework for the **ACME System 1** automation.  
The Dispatcher is responsible for logging into ACME System 1, retrieving all **Work Item 4 (WI4)** records, and exporting them into an Excel file.  
These records will later be used by the **Performer** to generate yearly reports and update the system.  

---

## 🎯 Goal  
- Automate the process of collecting **WI4 items** from ACME System 1  
- Store all retrieved items into an **Excel file** for further processing  

---

## 🛠️ Tools & Technologies  
- [UiPath Studio](https://www.uipath.com/product/studio)  
- UiPath Excel Activities  
- UiPath UI Automation Activities  
- REFramework Template  

---

## ⚙️ Workflow Steps  
1. **Log in** to ACME System 1 using credentials (email + password).  
2. **Navigate** to the Dashboard and open **Work Items**.  
3. **Extract all records** of type **WI4**.  
4. **Write the extracted records** into an Excel file.  
5. End process.  

---



## ▶️ How to Run  
1. Open the solution in **UiPath Studio**.  
2. Configure credentials for ACME System 1 in **Orchestrator Assets** or local Config.  
3. Run the **Dispatcher**.  
4. After completion, check `Data/WI4Items.xlsx` for the exported work items.  

---

## 📖 Learning Outcomes  
- Using REFramework for Dispatcher workflows  
- Automating web navigation with dynamic selectors  
- Extracting structured data from web applications  
- Writing business data into Excel for downstream automation  

---

### Documentation is included in the Documentation folder ###


### REFrameWork Template ###
**Robotic Enterprise Framework**

* Built on top of *Transactional Business Process* template
* Uses *State Machine* layout for the phases of automation project
* Offers high level logging, exception handling and recovery
* Keeps external settings in *Config.xlsx* file and Orchestrator assets
* Pulls credentials from Orchestrator assets and *Windows Credential Manager*
* Gets transaction data from Orchestrator queue and updates back status
* Takes screenshots in case of system exceptions


### How It Works ###

1. **INITIALIZE PROCESS**
 + ./Framework/*InitiAllSettings* - Load configuration data from Config.xlsx file and from assets
 + ./Framework/*GetAppCredential* - Retrieve credentials from Orchestrator assets or local Windows Credential Manager
 + ./Framework/*InitiAllApplications* - Open and login to applications used throughout the process

2. **GET TRANSACTION DATA**
 + ./Framework/*GetTransactionData* - Fetches transactions from an Orchestrator queue defined by Config("OrchestratorQueueName") or any other configured data source

3. **PROCESS TRANSACTION**
 + *Process* - Process trasaction and invoke other workflows related to the process being automated 
 + ./Framework/*SetTransactionStatus* - Updates the status of the processed transaction (Orchestrator transactions by default): Success, Business Rule Exception or System Exception

4. **END PROCESS**
 + ./Framework/*CloseAllApplications* - Logs out and closes applications used throughout the process


### For New Project ###

1. Check the Config.xlsx file and add/customize any required fields and values
2. Implement InitiAllApplications.xaml and CloseAllApplicatoins.xaml workflows, linking them in the Config.xlsx fields
3. Implement GetTransactionData.xaml and SetTransactionStatus.xaml according to the transaction type being used (Orchestrator queues by default)
4. Implement Process.xaml workflow and invoke other workflows related to the process being automated
