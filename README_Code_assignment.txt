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
  “2345”: [
    “2343225",
    “1223456”,
    “1233456"
  ],
  “2346”: [
    “3244332",
    “3244132”
  ]
}
{
  “2345": 3,
  “2346”: 2
}
The number of unique customerId for each geozone:
{
  “eu_west”: [
    “3244332”,
    “3244132"
  ],
  “us_east”: [
    “2343225"
  ],
  “us_west”: [
    “1223456",
    “1233456”
  ]
}
{
  “eu_west”: 2,
  “us_east”: 1,
  “us_west”: 2
}
The average build duration for each geozone:
{
  “eu_west”: [
    “4322",
    “4122”
  ],
  “us_east”: [
    “3445”
  ],
  “us_west”: [
    “2211”,
    “2221"
  ]
}
{
  “eu_west”: 4222.0,
  “us_east”: 3445.0,
  “us_west”: 2216.0
}
The list of unique customerId for each geozone:
{
  “eu_west”: [
    “3244332”,
    “3244132"
  ],
  “us_east”: [
    “2343225"
  ],
  “us_west”: [
    “1223456",
    “1233456”
  ]
}
[(0)root]: /