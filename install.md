## INSTALL INSTRUCTIONS

### Documenters Project

### Minh Anh Dang, Annie Wilcox, Ryan Hanks, Ryan Flanery, Samuel Corder

### Step 1: Scrape for Officials' Contact Information

1. If you don't have conda installed on your computer, follow the instructions on [this website](https://docs.conda.io/projects/conda/en/stable/index.html)
2. If you don't have Jupyter Notebook installed, use the command `conda install notebook` to install Jupyter Notebook.
3. Clone this notebook into an Anaconda Prompt terminal, and your preferred working directory by using ```git clone https://github.com/minh-msu/Detroit_Leadership_Dossiers.git```
4. Navigate to the repo with the command ```cd Detroit_Leadership_Dossiers```
5. Make a new environment using ```conda env create --prefix ./envs --file environment.yml```
6. Activate the environment ```conda activate ./envs```
8. Using the command `jupyter notebook Contact_Scraper.ipynb` navigate to the webscraping file.
9. Run the whole notebook, this notebook will read from ```List_of_names_1_7_2.xlsx``` and [this website](https://publish.smartsheet.com/9def816c9e6a4a4395d2903039bf714d) and merge the contact information into the dataframe derived from ```List_of_names_1_7_2.xlsx```
10. The resulting dataframe will be saved onto ```contact.csv```

### Step 2: Uploading Your Data to Google Sheets

1. Open the template for the dataset via [this link](https://docs.google.com/spreadsheets/d/1fpZTeWiMM9DN0RpZIrkl2MfY1Y7QcUBkwlxJSRlRGQQ/edit?gid=0#gid=0).
2. Click **File** &rarr; **Make A Copy**.
3. In your copy of our template, copy and paste all the contents of contacts.csv into cell B1. Column 'A' should be filled with the full names of each person in the dataset. (Note: It’s a lot of data, it might take a minute. If your computer asks if you want to save the clipboard, click **NO**. **Also:** If you have been working via the terminal/conda prompt shell thus far, it will be most efficient to open `contact.csv` as an excel file for this step.)
4. In the top right corner of the screen, click **Share**.
5. In the middle of your screen, click **Restricted** &rarr; **Anyone with the link** &rarr; **Done**. It is fine to leave share permisssions as view only.
6. Now that the data is publicly viewable, we need to grab the Sheet ID. The Sheet ID of your Google Sheet is the string after ```d/``` and before ```/edit?``` in the link to your Google Sheet. Copy your Sheet ID. You'll need it for our next step. (See image for reference of what the Sheet ID looks like) ![example](https://github.com/user-attachments/assets/271791e0-268d-4f5d-8847-ce645b16faa4) 

### Step 3: Updating the Code and Opening the Website

1. Open ```index.html```. In line 38, enter your Sheet ID. Save your changes.
2.  Open ```about.html```. In line 22, enter your Sheet ID. Save your changes.
3. Now, on the GitHub repository, click **Settings**
4. In the "Code and automation" section of the sidebar, click **Pages**.
5. Under "Build and deployment", under "Source", select **Deploy from a branch**.
6. Select the main branch, and leave the file as `/(root)`. It may take a second for the page to deploy, reload a few times if necessary.
7. Finally, you can view your version using the link GitHub provides you.
