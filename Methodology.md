#### Subdomain Enumeration 

subfinder -d actcorp.in -all -o sub ; chaos -d actcorp.in -o sub2 ; 
amass enum -passive -noalts -norecursive -d actcorp.in -o sub3 ; 
findomain -t actcorp.in -u sub4 ; crobat -s actcorp.in > sub5 ; 
gauplus -random-agent -subs actcorp.in | unfurl -u domains | anew sub6 ; 
waybackurls actcorp.in | unfurl -u domains | anew sub7

