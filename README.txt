# Guide to installing virlutils
# https://github.com/CiscoDevNet/virlutils

This is a project to save CML topologies for dCloud Topology Builder 


Steps to save a lab:

1) List all current labs using " cml ls" 


cisco@dcloud:~/CML$ cml ls
Labs on Server
╒══════════════════════════════════════╤═════════════════╤═══════════════╤═════════╤══════════╤═════════╤═════════╤══════════════╕
│ ID                                   │ Title           │ Description   │ Owner   │ Status   │   Nodes │   Links │   Interfaces │
╞══════════════════════════════════════╪═════════════════╪═══════════════╪═════════╪══════════╪═════════╪═════════╪══════════════╡
│ b87cbdca-bff1-4f0f-bad9-f60db1840c39 │ Multi-site 10.4 │               │ admin   │ STOPPED  │      15 │      30 │          210 │
├──────────────────────────────────────┼─────────────────┼───────────────┼─────────┼──────────┼─────────┼─────────┼──────────────┤
│ c391b9cc-575e-4a98-9b39-56266d2e7ce2 │ eBGP Fabric     │               │ admin   │ STARTED  │      11 │      22 │           66 │
├──────────────────────────────────────┼─────────────────┼───────────────┼─────────┼──────────┼─────────┼─────────┼──────────────┤
│ b807626e-7948-4470-b910-5e6ea62283d8 │ vPC Network     │               │ admin   │ STOPPED  │       5 │       7 │           39 │
╘══════════════════════════════════════╧═════════════════╧═══════════════╧═════════╧══════════╧═════════╧═════════╧══════════════╛


2) Set working lab using "cml use --id"

cml use --id  c391b9cc-575e-4a98-9b39-56266d2e7ce2 

3) Save the lab using "cml save"

CML save copies the current running configuration into the CML config. You can watch this process via the command line and check the 'CONFIG' tab in CML. 
The command also generates a topology file called 'topology.yaml' which you can then upload to git.

4) Add topology to Git
cisco@dcloud:~/CML$ git add topology.yaml 
cisco@dcloud:~/CML$ git commit -m "adding my first topology"
cisco@dcloud:~/CML$ git push
Username for 'https://github.com': carschmi@cisco.com
Password for 'https://carschmi%40cisco.com@github.com': 
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 2 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 8.27 KiB | 4.13 MiB/s, done.
Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/carschmi/CML/
   a217fe1..49b1bd6  main -> main


5) to push a lab to cml, use "cml up"
