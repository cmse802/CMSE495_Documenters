## INSTALL INSTRUCTIONS

### Documenters Project

### Minh Anh Dang, Annie Wilcox, Ryan Hanks, Ryan Flanery, Samuel Corder

### Step 1: Scrape for Officials' Contact Information

1. If you don't have conda installed on your computer, follow the instructions on [this website](https://conda-forge.org/download/)
3. Navigate ```https://github.com/minh-msu/Detroit_Leadership_Dossiers.git```. On the top right, between `Watch` and `Star`, click on the `Fork` button, and select `Create New Fork`.
4. Github should automatically redirect you to the forked repository. In the forked repository, select the green `Code` drop down menu, and copy the the HTTPS link by clicking the button shaped like two squares on the right of the link.
5. Now, open a conda prompt terminal, and clone your respository using the command `git clone (LINK YOU COPIED HERE)`.
6. Navigate to the repo with the command ```cd Detroit_Leadership_Dossiers```
7. Make a new environment using ```conda env create --prefix ./envs --file environment.yml```
8. Activate the environment ```conda activate ./envs```
10. Using the command `jupyter notebook backend/Contact_Scraper.ipynb` navigate to the webscraping file.
11. Run the whole notebook, this notebook will read from ```data/List_of_names_1_7_2.xlsx``` and [this website](https://publish.smartsheet.com/9def816c9e6a4a4395d2903039bf714d) and merge the contact information into the dataframe derived from ```data/List_of_names_1_7_2.xlsx```
12. The resulting dataframe will be saved onto ```data/contact.csv```

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
4. Under "Build and deployment", under "Source", select **Deploy from a branch**.
5. Select the main branch, and leave the file as `/(root)`. It may take a second for the page to deploy. 
6. Finally, you can view your version using the link `your_github_username.github.io/Detroit_Leadership_Dossiers`.
