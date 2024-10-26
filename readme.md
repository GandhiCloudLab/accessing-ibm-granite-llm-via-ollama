# Accessing IBM Granite LLM via Ollama

This document explores how to access the IBM Granite model using Ollama. Let's demonstrate this process using both Jupyter Notebook and a Python script.

<img src="images/arch.png">

## 1. Setup Ollama

Ollama is a tool designed to run and interact with large language models (LLMs) locally on your computer, rather than in the cloud. It provides a streamlined interface for deploying and managing models like IBM Granite or other compatible LLMs directly on local hardware.

1. Download and install Ollama app in your system by using the URL https://ollama.com/download

2. Start the Ollama app by using the below command

```
ollama serve
```

3. Download any Granite model into your system.

```
ollama pull granite3-dense:2b
```

4. Verify the downloaded model by using the below command.
```
ollama list
```

You should get the below output.

```
NAME             	ID          	SIZE  	MODIFIED
granite3-dense:2b	a9c7deef7ab8	1.6 GB	2 hours ago
```

5. You can also pull few other models as well.

```
ollama pull granite3-dense:8b
ollama pull granite-code:3b
ollama pull granite-code:8b
ollama pull granite-code:20b
```

Ollama is now ready to serve content from the downloaded LLM models.


## 2. Setup JupyterLab

Need to install the JupyterLab. It is always good to  install JupyterLab in an Python Virtual environment.


1. Goto a folder where you want to install JupyterLab

ex: 
```
cd /Users/gandhi/GandhiMain/998-work
```

2. Create a virtual environment `my-jupyter-env` and activate it by using the below command

```
python -m venv my-jupyter-env
source my-jupyter-env/bin/activate
```

3. Install jupyterlab using the below command
```
pip install jupyterlab 
```

4. Run jupyterlab using the below command

```
jupyter lab 
```
 
5. JupyterLab will start and open in a new browser window at the URL http://localhost:8888/lab/workspaces/auto-U

## 3. Create Jupyter Notebook with Python script

Let's create a Jupyter Notebook with Python script to access IBM Granite model.

### 3.1 Create Notebook

1. In the JupyterLab window, click on the + button in the top.

<img src="images/image-11.png">

2. Choose the `Notebook` tile  `Python 3 (ipykernel)` in the navigator window.

<img src="images/image-12.png">

3. Click on the `Save` button to save the notebook.

<img src="images/image-13.png">

4. Enter the name for the notebook.
5. Click `Rename` button

<img src="images/image-14.png">

The notebook is saved in the given name.

<img src="images/image-15.png">

### 3.2 Insert Scripts into the Notebook (For Experts)

This section is intended for experts. If you're new to notebooks, please skip this section and proceed to the next one.

1. Copy the content below into four separate cells in the notebook.

```
!pip install langchain-ollama
```

```
model_id = "granite3-dense:2b"
```

```
from langchain_ollama.llms import OllamaLLM
model = OllamaLLM(model=model_id)
```

```
prompt = "What is Kubernetes"

response = model.invoke(prompt)
print(response)
```

2. Verify the notebook look like this.

<img src="images/image-21.png">

The Notebook is created and let's run the notebook in the next section.


### 3.3 Insert Scripts into the Notebook (For Beginners)

This section is intended for beginners. If you're an expert, feel free to skip this section, and we hope you've completed the previous one.

<details><summary>CLICK me for detailed instructions</summary>

1. Copy the below content in the first cell.
```
!pip install langchain-ollama
```
<img src="images/image-16.png">

2. Click on + button in the Notebook 

<img src="images/image-17.png">

you get the second cell.

<img src="images/image-18.png">


3. Copy the below content in the second cell.

```
model_id = "granite3-dense:2b"
```

<img src="images/image-19.png">

4. Click on + button in the Notebook and copy the below content in the third cell.
```
from langchain_ollama.llms import OllamaLLM
model = OllamaLLM(model=model_id)
```
<img src="images/image-20.png">


5. Click on + button in the Notebook and copy the below content in the fourth cell.
```
prompt = "What is Kubernetes"

response = model.invoke(prompt)
print(response)
```

<img src="images/image-21.png">

The Notebook is created and let's run the notebook in the next section.

</details>

## 4. Execute the Jupyter Notebook

Let's execute the notebook.


### 4.1. Check Kernal

1. Ensure the kernel is pointing to `Python 3 (ipykernel)` in the top right corner.

<img src="images/image-22.png">

### 4.2 Execute Notebook (For Experts)

This section is intended for experts. If you're new to notebooks, please skip this section and proceed to the next one.

1. Run all the four cells to see the output.

<img src="images/image-28.png">

We have successfully executed the notebook by calling the IBM Granite model via ollama.

### 4.3 Execute Notebook (For Beginners)

This section is intended for beginners. If you're an expert, feel free to skip this section, and we hope you've completed the previous one.

<details><summary>CLICK ne for detailed instructions</summary>

1. Place the cursor in the first cell 

2. Click on the `Run the cell and advance` button.

This would install the `langchain-ollama`

<img src="images/image-23.png">

Here is the output of that.

<img src="images/image-24.png">

3. Similarly run the second cell.

This will choose the model_id 
<img src="images/image-25.png">

4. Run the third cell.

This will create model object instance.

<img src="images/image-26.png">

5. Run the fourth cell.

This will call the IBM Granite model and print the response.

<img src="images/image-27.png">

We have successfully executed the notebook by calling the IBM Granite model via ollama.

<img src="images/image-28.png">
</details>

## 5. Sample Notebook

The same script is available as `sample.ipynb` notebook along with markup document [here](../files/sample.ipynb). You can copy and paste the notebook/content and execute it.

<img src="images/image-29.png">

## 6. Closing the Apps

You can close the environment by following the steps here.

### 6.1 Close JupyterLab

1. You can close the window by choosing `File > Shutdown` option from the menu.

    <img src="images/image-30.png">

OR 

2. Press `Ctrl + C` keys to stop the JupyterLab from the terminal window.

### 6.2 Deactivate Virtual Environment

1. Run the below command to deactivate the virtual environment.

```
deactivate
```

### 6.3 Stop Ollama

1. Goto the terminal window, where your Ollama is running and press `Ctrl + C`

OR 

2. Run the below command to know the PID of the Ollama app.

```
ps aux | grep ollama
```

3. Run the below command to kill the Ollama app process.

```
kill -9 <PID>
```


