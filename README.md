# Trade Data

[Overview](https://model.earth/profile/trade/)

Receives data from [exiobase/tradeflow](https://model.earth/exiobase/tradeflow/) and [exiobase/tradeflow/bea](https://model.earth/exiobase/tradeflow/bea/) 

This [EPA download page](https://catalog.data.gov/dataset/useeio-models-with-import-emission-factors-for-greenhouse-gases-for-2017-2022-from-exiobas) is helpful for clarifying the difference between commodities, BEA service categories and sectors. (3 files from that page were added to concordance folder here, not sure if that's 2 or 3 of the files above. Might be more to use.)

It includes these crosswalks:  
(1) EXIOBASE commodities to USEEIO commodities.  
(2) BEA service category data to USEEIO sectors.  
(3) EXIOBASE Country/Region to BEA Service, Census Goods and TiVA trade regions.  

The differences between "CEDA Sector" and the new USEEIO_Detail 2017 sector are small.  
"CEDA Sector" and "USEEIO_Detail 2012" both correspond to NAICS 2012. 
Whereas USEEIO_Detail 2017 split Aluminum into 2 categories and combined 4 Appliance categories. (See notes below)

**Conclusions:**

CEDA is too limited for us to use since it only provides emission data, and doesn't convey the 2017 NAICS splits and merges done by the US EPA for USEEIO2.

We don't use industry_id for the USEEIO or BEA values since neither refer to their data as Industry. (Though it is NAICS industry categories with minor modifications.)

Hence, for easy table names with the Exiobase data, we use "industry" (5-char) and "commodity" (6-char).

There are too many meanings for "sector" to warrant giving it a table. (Plus sector IDs change every 5 years.)  "beasummary" is more clear.

The crosswalks above correspond to the US EPA reports here:

https://model.earth/exiobase/tradeflow/bea/

You could focus on running our bea scripts above to create .csv files so we can review before SQL tables are created, and also add the crosswalks from the first link above to our trade-data repo.


**NOTES**. 
CEDA still uses NAICS 2012:

[This ceda_to_useeio_commodity concordance](https://pasteur.epa.gov/uploads/10.23719/1531906/documents/ceda_to_useeio_commodity_concordance.csv) provides the 2012, CEDA Sector, and 2017


NAICS USEEIO_Detail 2017 has these differences:

Household Appliance Consolidation:
The 2012 NAICS Codes 335221, 335222, 335224 and 335228 for Household Cooking Appliance, Household Refrigerator and Home Freezer, Household Laundry Equipment and Other Major Household Appliance Manufacturing are all combined in 2017 to the single NAICS Code: 335220, "Major Household Appliance Manufacturing" by the U.S. Environmental Protection Agency.

Aluminum Manufacturing:
The 2012 NAICS Code 331313 was split into 2017 NAICS 331313 and 33131B for reclassification in the aluminum manufacturing sector, where CEDA retains the older detailed classification while USEEIO 2017 uses a modified code (33131B).