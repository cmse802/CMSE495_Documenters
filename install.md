## INSTALL INSTRUCTIONS

### Documenters Project

### Minh Anh Dang, Annie Wilcox, Ryan Hanks, Ryan Flanery, Samuel Corder

### Step 0: Manually Collected Data
1. The team was provided with this file: [```data/List_of_names_1_7_2.xlsx```](data/List_of_names_1_7_2.xlsx) with all these filled out: Name (Prefix, First, Middle, Last, Suffix), Title, Department/District, and Board/Commission/Department.
2. All the LinkedIn handles were manually collected using the committee's name and title, and double-checked from their profile.
3. All the X/Twitter handles are found by feeding all available information of a committee into the Grok AI and manually inputted back into the csv file

### Step 1: Extract Officials' Contact Information

1. If you don't have conda installed on your computer, follow the instructions on [this website](https://conda-forge.org/download/)
3. Navigate to ```https://github.com/minh-msu/Detroit_Leadership_Dossiers.git```. On the top right, between `Watch` and `Star`, click on the `Fork` button, and select `Create New Fork`.
4. Github should automatically redirect you to the forked repository. In the forked repository, select the green `Code` drop down menu, and copy the the HTTPS link by clicking the button shaped like two squares on the right of the link.
5. Now, open a conda prompt terminal, and clone your respository using the command `git clone (LINK YOU COPIED HERE)`.
6. Navigate to the repo with the command ```cd Detroit_Leadership_Dossiers```
7. Make a new environment using ```conda env create --prefix ./envs --file environment.yml```. This will take a while. 
8. Activate the environment ```conda activate ./envs```
9. Either run ```jupyter lab``` or ```jupyter notebook``` to open a Jupyter window with the new environment
10. Navigate to [```backend/Contact_Scraper.ipynb```](backend/Contact_Scraper.ipynb)
11. In the ```Kernel``` tab, choose ```Restart Kernel and Run All Cells...```
12. This notebook will read from [```data/List_of_names_1_7_2.xlsx```](data/List_of_names_1_7_2.xlsx) and [this website](https://publish.smartsheet.com/9def816c9e6a4a4395d2903039bf714d) and merge the contact information into the dataframe derived from ```data/List_of_names_1_7_2.xlsx```
13. The resulting dataframe will be saved onto [```data/contact.csv```](data/contact.csv).
14. There is already a ```data/contact.csv``` file ready to be used in this repository. However, if you believe that there's an update to the City of Detroit contact information website, push the new file by navigating to the opened conda prompt terminal, run ```git pull```, then ```git add data/contact.csv```, then ```git commit -m "Update data/contact.csv file"```, and finally git push. 

### Step 2: Uploading Your Data to Google Sheets

1. Open the template for the dataset via [this link](https://docs.google.com/spreadsheets/d/1fpZTeWiMM9DN0RpZIrkl2MfY1Y7QcUBkwlxJSRlRGQQ/edit?gid=0#gid=0).
2. Click **File** &rarr; **Make A Copy**.
3. In your copy of our template, copy and paste all the contents of contacts.csv into cell B1. Column 'A' should be filled with the full names of each person in the dataset. (Note: It’s a lot of data, it might take a minute. If your computer asks if you want to save the clipboard, click **NO**. **Also:** If you have been working via the terminal/conda prompt shell thus far, it will be most efficient to open `contact.csv` as an excel file for this step.)
4. In the top right corner of the screen, click **Share**.
5. In the middle of your screen, click **Restricted** &rarr; **Anyone with the link** &rarr; **Done**. It is fine to leave share permisssions as view only.
6. Now that the data is publicly viewable, we need to grab the Sheet ID. The Sheet ID of your Google Sheet is the string after ```d/``` and before ```/edit?``` in the link to your Google Sheet. Copy your Sheet ID. You'll need it for our next step. (See image for reference of what the Sheet ID looks like) ![example](https://github.com/user-attachments/assets/271791e0-268d-4f5d-8847-ce645b16faa4) 

### Step 3: Updating the Code and Opening the Website

1. In your forked repository (via the GitHub web interface), open ```script.js```. In line 2, update the variable `SHEET_ID` with the ID you copied from the template (copy and paste your ID in the quotations on line 2) and your API key in the line below(line 3). Commit your changes.
2. Now, on the GitHub repository, click **Settings**
3. In the "Code and automation" section of the sidebar, click **Pages**.
4. Select the main branch, and leave the file as `/(root)`. 
5. Under "Build and deployment", under "Source", select **Deploy from a branch**. It may take a second for the page to deploy
6. Finally, you can view your version using the link `your_github_username.github.io/Detroit_Leadership_Dossiers`.

### Step 4 (Extra): Scrape for Officials' Contribution Record
1. In the Jupyter window opened in Step 1, navigate to [backend/Finance_Scraper.ipynb](backend/Finance_Scraper.ipynb)
2. In the ```Kernel``` tab, choose ```Restart Kernel...```
3. Run the first code block ```Imports```
4. If you want to test the scraping function, run all the code blocks in the ```Scraping``` subheading, else skip ahead. This part will scrape from the [Wayne County Finance system](https://wccampaignfinance.com/Public/ReceiptsList) for committees' contribution records and saves them into a CSV file called [data/contributions.csv](../data/contributions.csv). If you want to create a brand new contribution records dataset, uncomment the last line in the last code block (```df.to_csv('../data/contributions.csv', index=False)```).
5. Run all the code blocks in the ```Visualization``` subheading, this will generate pie charts with dynamic hovering for a provided committee's name. Change the parameter in the ```make_dynamic_chart()``` function if you want to test run it with other names. 
6. The data and pie charts obtained from this notebook have not been integrated into the frontend yet.
