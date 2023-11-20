# IMPORT BEAUTIFULSOUP

from bs4 import BeautifulSoup


# In[2]: IMPORT REQUESTS

import requests


# In[3]: BRINGING DATA FROM SOURCE IN HTML FORMAT 


url = 'https://en.wikipedia.org/wiki/List_of_largest_companies_in_the_United_States_by_revenue'
page = requests.get(url)
soup = BeautifulSoup(page.text, 'html')


# In[4]:


print(soup)


# In[5]: FIND OUT ALL THE TABLE DATA IN HTML CODES


soup.find_all('table')[1]


# In[6]:


soup.find('table', class_ = 'wikitable sortable')


# In[7]:


table = soup.find_all('table')[1]


# In[8]:


print(table)


# In[9]:


world_title= table.find_all('th')


# In[10]:


world_title


# In[11]: STRIPING THE TITLE OF EACH COLUMNS INTO TEXT 


W_t_t= [title.text.strip() for title in world_title]


# In[12]:


#world_table_titles = [title.text.strip() for title in world_titles]

print(W_t_t)


# In[13]:IMPORT PANDAS TO STRUCTURE DATA AND MAKE CHANGES IN FORMAT 


import pandas as pd


# In[14]:


df = pd.DataFrame(columns = W_t_t)

df


# In[15]:


column_data=table.find_all('tr')


# In[16]:NOW ARRANGING DATA AS PER COLUMN STANDARD


for row in column_data[1:]:
    row_data=row.find_all('td')
    individual_row_data= [data.text.strip() for data in row_data]
    
    length = len(df)
    df.loc[length]=individual_row_data


# In[17]:


df


# In[18]:NOW SAVING THE DATA LOCALLY IN EXCEL FORMAT


df.to_excel(r'C:\Users\ASUS\OneDrive\projects.xlsx', index=False)

