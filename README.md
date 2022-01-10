# Prasanna

********************************************************************************************************************
SUMMARY
********************************************************************************************************************
Here is the detailed information of code execution:
- Code is written using Python on linux Platform
- Python script file is <codeassignment.py>

In cmd prompt RUN as below, so that the expected output displays on the screen.
./codeassignment.py <enter>


********************************************************************************************************************
EXECUTION RESULT
********************************************************************************************************************
[(0)root}: /
# ./nagendra.py

Single String with multi line is :
2343225,2345,us_east,RedTeam,ProjectApple,3445s
1223456,2345,us_west,BlueTeam,ProjectBanana,2211s
3244332,2346,eu_west,YellowTeam3,ProjectCarrot,4322s
1233456,2345,us_west,BlueTeam,ProjectDate,2221s
3244132,2346,eu_west,YellowTeam3,ProjectEgg,4122s 

The number of unique customerId for each contractId:
{
    "2345": [
        "2343225",
        "1223456",
        "1233456"
    ],
    "2346": [
        "3244332",
        "3244132"
    ]
}
{
    "2345": 3,
    "2346": 2
}
The number of unique customerId for each geozone:
{
    "eu_west": [
        "3244332",
        "3244132"
    ],
    "us_east": [
        "2343225"
    ],
    "us_west": [
        "1223456",
        "1233456"
    ]
}
{
    "eu_west": 2,
    "us_east": 1,
    "us_west": 2
}
The average build duration for each geozone:
{
    "eu_west": [
        "4322",
        "4122"
    ],
    "us_east": [
        "3445"
    ],
    "us_west": [
        "2211",
        "2221"
    ]
}
{
    "eu_west": 4222.0,
    "us_east": 3445.0,
    "us_west": 2216.0
}
The list of unique customerId for each geozone:
{
    "eu_west": [
        "3244332",
        "3244132"
    ],
    "us_east": [
        "2343225"
    ],
    "us_west": [
        "1223456",
        "1233456"
    ]
}

[(0)root]: /
# 


********************************************************************************************************************
CODE in python script <codeassignment.py>
********************************************************************************************************************
#!/usr/bin/python
import re
import json

data="""2343225,2345,us_east,RedTeam,ProjectApple,3445s
1223456,2345,us_west,BlueTeam,ProjectBanana,2211s
3244332,2346,eu_west,YellowTeam3,ProjectCarrot,4322s
1233456,2345,us_west,BlueTeam,ProjectDate,2221s
3244132,2346,eu_west,YellowTeam3,ProjectEgg,4122s"""

print("\nSingle String with multi line is :\n%s \n"%data)

#2343225,2345,us_east,RedTeam,ProjectApple,3445s ->   this line is the refference to write the regular expression as below
regex = r"(\d+),(\d+),(\w+_\w+),(\w+),(\w+),(\d+)(s)"
data_dict={}
contractId_dict={}
geozone_dict={}
geozone_dict_lst={}
teamcode_dict={}
projectcode_dict={}
buildduration_dict={}

for line in data.split('\n'):        #We are iterating over the splitted string list to fetch the raw data in to the Dictionary
        line=line.strip()
        RGX=re.compile(regex)
        match = RGX.search(line)
        if match != None:
                #fetching the re groups info into required variables
                customerId=match.group(1)
                contractId=match.group(2)
                geozone=match.group(3)
                teamcode=match.group(4)
                projectcode=match.group(5)
                buildduration=match.group(6)

                #The number of unique customerId for each ContractID
                if contractId not in contractId_dict:
                        contractId_dict[contractId]=[customerId]
                else:
                        contractId_dict[contractId]+=[customerId]

                #The number of unique customerId for each geozone
                if geozone not in geozone_dict:
                        geozone_dict[geozone]=[customerId]
                else:
                        geozone_dict[geozone]+=[customerId]

                #The average buildduration for each geozone
                if geozone not in buildduration_dict:
                        buildduration_dict[geozone]=[buildduration]
                else:
                        buildduration_dict[geozone]+=[buildduration]

                #The list of unique customerId for each geozone
                if geozone not in geozone_dict_lst:
                        geozone_dict_lst[geozone]=[customerId]
                else:
                        geozone_dict_lst[geozone]+=[customerId]

print("The number of unique customerId for each contractId:")
print (json.dumps(contractId_dict, sort_keys=True, indent=4))  #need to be wiped off
contractId_dict_count={}
for cntr_id in contractId_dict:
        contractId_dict_count[cntr_id]=len(contractId_dict[cntr_id])
print (json.dumps(contractId_dict_count, sort_keys=True, indent=4))

print("The number of unique customerId for each geozone:")
print (json.dumps(geozone_dict, sort_keys=True, indent=4))      #need to be wiped off
geozone_dict_count={}
for geozone in geozone_dict:
        geozone_dict_count[geozone]=len(geozone_dict[geozone])
print (json.dumps(geozone_dict_count, sort_keys=True, indent=4))

print("The average buildduration for each geozone:")
print (json.dumps(buildduration_dict, sort_keys=True, indent=4))
avg_buildduration_dict={}
for geozone in buildduration_dict:
        avg_buildduration_dict[geozone]=sum([int(elmnt) for elmnt in buildduration_dict[geozone]])/len(buildduration_dict[geozone])
print (json.dumps(avg_buildduration_dict, sort_keys=True, indent=4))

print("The list of unique customerId for each geozone:")
print (json.dumps(geozone_dict_lst, sort_keys=True, indent=4))

*************************************************************************************************************************************************************************************************
