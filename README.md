# YACS.n

![](https://github.com/YACS-RCOS/yacs.n/workflows/CI/badge.svg)
[![CodeFactor](https://www.codefactor.io/repository/github/yacs-rcos/yacs.n/badge)](https://www.codefactor.io/repository/github/yacs-rcos/yacs.n)
[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)
[![codecov](https://codecov.io/gh/YACS-RCOS/yacs.n/branch/master/graph/badge.svg)](https://codecov.io/gh/YACS-RCOS/yacs.n)

YACS with support for multi and sub-semesters for any school

## YACS at your school?

Clone the repo and

`scripts/start.sh`

Once up,

Head to the admin panel at `/admin`

You'll be able to

1. Import courses
2. Select default semesters
3. Rename semester parts (useful for semesters that are split in parts)

Head to `/` and allow your peers/students to schedule away!

## Development

You should have docker installed on your machine

**1. Run**

```bash
bash scripts/dev-start.sh
```

You should be able to access @ `localhost`

**2. Populate with your schools data**

In `localhost/admin` submit your school's courses by CSV and you're ready to schedule!

For schema see /rpi_data/summer-2020.csv as an example

**3. Different API Routes**

API is up
https://yacs.cs.rpi.edu/api/

Get Class:
Https://yacs.cs.rpi.edu/api/class?semester={}&search={}

Get department:
https://yacs.cs.rpi.edu/api/department

Get semester:
https://yacs.cs.rpi.edu/api/semester

Get semester info: 
https://yacs.cs.rpi.edu/api/semesterInfo

Get default semester: 
https://yacs.cs.rpi.edu/api/defaultsemester



