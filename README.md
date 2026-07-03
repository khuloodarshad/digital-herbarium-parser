# digital-herbarium-parser
A Python tool for M.Sc. botany data: standardizing messy field notes into digital herbarium catalogs.
import pandas as pd
import io

# 1. Messy field notes data
data = """Field_No,Collector,Local_Name,Scientific_Name,Date,Location,Medicinal_Use
101,Dr. A. Sharma,Neem,azadirachta INDICA,2026/03/12,"Kanpur, India",Antiseptic
102,R. Singh,Tulsi,  ocimum sanctum  ,15-04-2026,"Lucknow, India",Immunity
103,Dr. A. Sharma,Ashwagandha,withania somnifera,2026-05-20,"Delhi, India",Stress relief"""

# 2. Reading data into pandas
df = pd.read_csv(io.StringIO(data))

# 3. Botanical Data Standardization
df['Scientific_Name'] = df['Scientific_Name'].str.strip().str.capitalize()
df['Date'] = pd.to_datetime(df['Date'], format='mixed').dt.strftime('%Y-%m-%d')
df['Institution_Code'] = 'HERB-MSC-2026'

# 4. Organizing layout
ordered_columns = ['Institution_Code', 'Field_No', 'Scientific_Name', 'Local_Name', 'Date', 'Location', 'Medicinal_Use']
df_cleaned = df[ordered_columns]

# 5. Output
df_cleaned.to_csv('cleaned_herbarium_records.csv', index=False)
print("✨ Digital Herbarium Catalog Generated Successfully!")
print(df_cleaned.to_string())
