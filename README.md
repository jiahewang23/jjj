# 1. From data a_paycost
## 1.1 Generate the variable a_cost which is the numeric data.
### 1.1.1 Generate the variable which the range and pick the Maximum one.
    generate a_cost1 = real(regexs(1)) if regexm(subinstr(a_paycosts, ",", "", .), "[0-9]+ - ([0-9]+(\.[0-9]+)?)")  

### 1.1.2 Generate the variable which is the scalar.
    generate a_cost2 = real(regexs(1)) if regexm(subinstr(a_paycosts, ",", "", .), "^([0-9]+(\.[0-9]+)?)$")

### 1.1.3 Generate the variable which sets 0 when its element is "No", and set "." when its element is "Missing", "Yes" or "Indefinite".
````
generate a_cost3 = .
replace a_cost3 = 0 if a_paycosts == "No"
````
### 1.1.4 Combine the variable together and get variable a_paycost which type is "float".
````
generate a_cost = a_cost1
replace a_cost = a_cost2 if a_cost2 != .
replace a_cost = a_cost3 if a_cost3 != .
format a_cost %9.2f
drop a_cost1 a_cost2 a_cost3
````

## 1.2 Generate the variable a_anycost which is the dummy variable. the type is "float"
###  1.2.1 Generate the variable which set "1" when its element is "number","range" and "yes", set "0" when its element is "no", set "." when its element is "NA","Indefinite", "indefinite"
````
generate a_anycost = 1
replace a_anycost = 0 if a_paycosts == "No"
replace a_anycost = . if a_paycosts == "NA"
replace a_anycost = . if a_paycosts == "Indefinite"
replace a_anycost = . if a_paycosts == "indefinite"
````

## 1.3 Find all the elements that have special character such as "$44,000" or "over 44000" and Manual entry value as "44000"
````
generate special_character = regexm(a_paycosts, "[^,.0-9-YesNoNA]")

drop special_character
````


# 2. From data a_fine
## 2.1 Generate the variable a_finenumeric which is the numeric data.
````
generate a_finenumeric1 = real(regexs(1)) if regexm(subinstr(a_fine, ",", "", .), "[0-9]+ - ([0-9]+(\.[0-9]+)?)")

generate a_finenumeric2 = real(regexs(1)) if regexm(subinstr(a_fine, ",", "", .), "^([0-9]+(\.[0-9]+)?)$")

generate a_finenumeric3 = .
replace a_finenumeric3 = 0 if a_fine == "No"

generate a_finenumeric = a_finenumeric1
replace a_finenumeric = a_finenumeric2 if a_finenumeric2 != .
replace a_finenumeric = a_finenumeric3 if a_finenumeric3 != .
format a_finenumeric %9.2f
drop a_finenumeric1 a_finenumeric2 a_finenumeric3
````
## 2.2 Generate the variable a_finedummy which is the dummy data
````
generate a_finedummy = 1
replace a_finedummy = 0 if a_fine == "No"
replace a_finedummy = . if a_fine == "NA"
replace a_finedummy = . if a_fine == "Indefinite"
replace a_finedummy = . if a_fine == "indefinite"
````
## 2.3 Find all the elements that have special character
````
generate special_character = regexm(a_fine, "[^,.0-9-YesNoNA]")

drop special_character
````

# 3. From data a_reprimand
## 3.1 Generate the variable a_reprimandnumeric which is the numeric data.
````
generate a_reprimandnumeric1 = real(regexs(1)) if regexm(subinstr(a_reprimand, ",", "", .), "[0-9]+ - ([0-9]+(\.[0-9]+)?)")  

generate a_reprimandnumeric2 = real(regexs(1)) if regexm(subinstr(a_reprimand, ",", "", .), "^([0-9]+(\.[0-9]+)?)$")

generate a_reprimandnumeric3 = .
replace a_reprimandnumeric3 = 0 if a_reprimand == "No"

generate a_reprimandnumeric = a_reprimandnumeric1
replace a_reprimandnumeric = a_reprimandnumeric2 if a_reprimandnumeric2 != .
replace a_reprimandnumeric = a_reprimandnumeric3 if a_reprimandnumeric3 != .
format a_reprimandnumeric %9.2f
drop a_reprimandnumeric1 a_reprimandnumeric2 a_reprimandnumeric3
````
## 3.2 Generate the variable a_reprimanddummy which is the dummy data
````
generate a_reprimanddummy = 1
replace a_reprimanddummy = 0 if a_reprimand == "No"
replace a_reprimanddummy = . if a_reprimand == "NA"
replace a_reprimanddummy = . if a_reprimand == "Indefinite"
replace a_reprimanddummy = . if a_reprimand == "indefinite"
````
## 3.3 Find all the elements that have special character
````
generate special_character = regexm(a_reprimand, "[^,.0-9-YesNoNA]")

drop special_character
````
# 4. From data a_supervision
## 4.1 Generate the variable a_supervisionnumeric which is the numeric data.
````
generate a_supervisionnumeric1 = real(regexs(1)) if regexm(subinstr(a_supervision, ",", "", .), "[0-9]+ - ([0-9]+(\.[0-9]+)?)")  

generate a_supervisionnumeric2 = real(regexs(1)) if regexm(subinstr(a_supervision, ",", "", .), "^([0-9]+(\.[0-9]+)?)$")

generate a_supervisionnumeric3 = .
replace a_supervisionnumeric3 = 0 if a_supervision == "No"

generate a_supervisionnumeric = a_supervisionnumeric1
replace a_supervisionnumeric = a_supervisionnumeric2 if a_supervisionnumeric2 != .
replace a_supervisionnumeric = a_supervisionnumeric3 if a_supervisionnumeric3 != .
format a_supervisionnumeric %9.2f
drop a_supervisionnumeric1 a_supervisionnumeric2 a_supervisionnumeric3
````
## 4.2 Generate the variable a_supervisiondummy which is the dummy data
````
generate a_supervisiondummy = 1
replace a_supervisiondummy = 0 if a_supervision == "No"
replace a_supervisiondummy = . if a_supervision == "NA"
replace a_supervisiondummy = . if a_supervision == "Indefinite"
replace a_supervisiondummy = . if a_supervision == "indefinite"
````
## 4.3 Find all the elements that have special character
````
generate special_character = regexm(a_supervision, "[^,.0-9-YesNoNA]")

drop special_character
````

# 5. From data a_assessment
## 5.1 Generate the variable a_assessmentnumeric which is the numeric data.
````
generate a_assessmentnumeric1 = real(regexs(1)) if regexm(subinstr(a_assessment, ",", "", .), "[0-9]+ - ([0-9]+(\.[0-9]+)?)")  

generate a_assessmentnumeric2 = real(regexs(1)) if regexm(subinstr(a_assessment, ",", "", .), "^([0-9]+(\.[0-9]+)?)$")

generate a_assessmentnumeric3 = .
replace a_assessmentnumeric3 = 0 if a_assessment == "No"

generate a_assessmentnumeric = a_assessmentnumeric1
replace a_assessmentnumeric = a_assessmentnumeric2 if a_assessmentnumeric2 != .
replace a_assessmentnumeric = a_assessmentnumeric3 if a_assessmentnumeric3 != .
format a_assessmentnumeric %9.2f
drop a_assessmentnumeric1 a_assessmentnumeric2 a_assessmentnumeric3
````

## 5.2 Generate the variable a_assessmentdummy which is the dummy data
````
generate a_assessmentdummy = 1
replace a_assessmentdummy = 0 if a_assessment == "No"
replace a_assessmentdummy = . if a_assessment == "NA"
replace a_assessmentdummy = . if a_assessment == "Indefinite"
replace a_assessmentdummy = . if a_assessment == "indefinite"
````
## 5.3 Find all the elements that have special character
````
generate special_character = regexm(a_assessment, "[^,.0-9-YesNoNA]")

drop special_character
````
# 6. From data a_community
## 6.1 Generate the variable a_communitynumeric which is the numeric data.
````
generate a_communitynumeric1 = real(regexs(1)) if regexm(subinstr(a_community, ",", "", .), "[0-9]+ - ([0-9]+(\.[0-9]+)?)")  

generate a_communitynumeric2 = real(regexs(1)) if regexm(subinstr(a_community, ",", "", .), "^([0-9]+(\.[0-9]+)?)$")

generate a_communitynumeric3 = .
replace a_communitynumeric3 = 0 if a_community == "No"

generate a_communitynumeric = a_communitynumeric1
replace a_communitynumeric = a_communitynumeric2 if a_communitynumeric2 != .
replace a_communitynumeric = a_communitynumeric3 if a_communitynumeric3 != .
format a_communitynumeric %9.2f
drop a_communitynumeric1 a_communitynumeric2 a_communitynumeric3
````
## 6.2 Generate the variable a_communitydummy which is the dummy data
````
generate a_communitydummy = 1
replace a_communitydummy = 0 if a_community == "No"
replace a_communitydummy = . if a_community == "NA"
replace a_communitydummy = . if a_community == "Indefinite"
replace a_communitydummy = . if a_community == "indefinite"
````
## 6.3 Find all the elements that have special character
````
generate special_character = regexm(a_community, "[^,.0-9-YesNoNA]")

drop special_character
````

# 7. From data a_probation
## 7.1 Generate the variable a_probationnumeric which is the numeric data.
````
generate a_probationnumeric1 = real(regexs(1)) if regexm(subinstr(a_probation, ",", "", .), "[0-9]+ - ([0-9]+(\.[0-9]+)?)")  

generate a_probationnumeric2 = real(regexs(1)) if regexm(subinstr(a_probation, ",", "", .), "^([0-9]+(\.[0-9]+)?)$")

generate a_probationnumeric3 = .
replace a_probationnumeric3 = 0 if a_probation == "No"

generate a_probationnumeric = a_probationnumeric1
replace a_probationnumeric = a_probationnumeric2 if a_probationnumeric2 != .
replace a_probationnumeric = a_probationnumeric3 if a_probationnumeric3 != .
format a_probationnumeric %9.2f
drop a_probationnumeric1 a_probationnumeric2 a_probationnumeric3
````
## 7.2 Generate the variable a_probationdummy which is the dummy data
````
generate a_probationdummy = 1
replace a_probationdummy = 0 if a_probation == "No"
replace a_probationdummy = . if a_probation == "NA"
replace a_probationdummy = . if a_probation == "Indefinite"
replace a_probationdummy = . if a_probation == "indefinite"
````
## 7.3 Find all the elements that have special character
````
generate special_character = regexm(a_probation, "[^,.0-9-YesNoNA]")

drop special_character
````
# 8. From data a_education
## 8.1 Generate the variable a_educationnumeric which is the numeric data.
````
generate a_educationnumeric1 = real(regexs(1)) if regexm(subinstr(a_education, ",", "", .), "[0-9]+ - ([0-9]+(\.[0-9]+)?)")  

generate a_educationnumeric2 = real(regexs(1)) if regexm(subinstr(a_education, ",", "", .), "^([0-9]+(\.[0-9]+)?)$")

generate a_educationnumeric3 = .
replace a_educationnumeric3 = 0 if a_education == "No"

generate a_educationnumeric = a_educationnumeric1
replace a_educationnumeric = a_educationnumeric2 if a_educationnumeric2 != .
replace a_educationnumeric = a_educationnumeric3 if a_educationnumeric3 != .
format a_educationnumeric %9.2f
drop a_educationnumeric1 a_educationnumeric2 a_educationnumeric3
````
## 8.2 Generate the variable a_educationdummy which is the dummy data
````
generate a_educationdummy = 1
replace a_educationdummy = 0 if a_education == "No"
replace a_educationdummy = . if a_education == "NA"
replace a_educationdummy = . if a_education == "Indefinite"
replace a_educationdummy = . if a_education == "indefinite"
````
## 8.3 Find all the elements that have special character
````
generate special_character = regexm(a_education, "[^,.0-9-YesNoNA]")

drop special_character
````
# 9. From data a_voluntary_relinquish
## 9.1 Generate the variable a_voluntary_relinquishnumeric which is the numeric data.
````
generate a_voluntary_relinquishnumeric1 = real(regexs(1)) if regexm(subinstr(a_voluntary_relinquish, ",", "", .), "[0-9]+ - ([0-9]+(\.[0-9]+)?)")  

generate a_voluntary_relinquishnumeric2 = real(regexs(1)) if regexm(subinstr(a_voluntary_relinquish, ",", "", .), "^([0-9]+(\.[0-9]+)?)$")

generate a_voluntary_relinquishnumeric3 = .
replace a_voluntary_relinquishnumeric3 = 0 if a_voluntary_relinquish == "No"

generate a_voluntary_relinquishnumeric = a_voluntary_relinquishnumeric1
replace a_voluntary_relinquishnumeric = a_voluntary_relinquishnumeric2 if a_voluntary_relinquishnumeric2 != .
replace a_voluntary_relinquishnumeric = a_voluntary_relinquishnumeric3 if a_voluntary_relinquishnumeric3 != .
format a_voluntary_relinquishnumeric %9.2f
drop a_voluntary_relinquishnumeric1 a_voluntary_relinquishnumeric2 a_voluntary_relinquishnumeric3
````
## 9.2 Generate the variable a_voluntary_relinquishdummy which is the dummy data
````
generate a_voluntary_relinquishdummy = 1
replace a_voluntary_relinquishdummy = 0 if a_voluntary_relinquish == "No"
replace a_voluntary_relinquishdummy = . if a_voluntary_relinquish == "NA"
replace a_voluntary_relinquishdummy = . if a_voluntary_relinquish == "Indefinite"
replace a_voluntary_relinquishdummy = . if a_voluntary_relinquish == "indefinite"
````
## 9.3 Find all the elements that have special character
````
generate special_character = regexm(a_voluntary_relinquish, "[^,.0-9-YesNoNA]")

drop special_character
````

# 10. From data a_discipline_relinquish
## 10.1 Generate the variable a_discipline_relinquishnumeric which is the numeric data.
````
generate a_discipline_relinquishnumeric1 = real(regexs(1)) if regexm(subinstr(a_discipline_relinquish, ",", "", .), "[0-9]+ - ([0-9]+(\.[0-9]+)?)")  

generate a_discipline_relinquishnumeric2 = real(regexs(1)) if regexm(subinstr(a_discipline_relinquish, ",", "", .), "^([0-9]+(\.[0-9]+)?)$")

generate a_discipline_relinquishnumeric3 = .
replace a_discipline_relinquishnumeric3 = 0 if a_discipline_relinquish == "No"

generate a_discipline_relinquishnumeric = a_discipline_relinquishnumeric1
replace a_discipline_relinquishnumeric = a_discipline_relinquishnumeric2 if a_discipline_relinquishnumeric2 != .
replace a_discipline_relinquishnumeric = a_discipline_relinquishnumeric3 if a_discipline_relinquishnumeric3 != .
format a_discipline_relinquishnumeric %9.2f
drop a_discipline_relinquishnumeric1 a_discipline_relinquishnumeric2 a_discipline_relinquishnumeric3
````
## 10.2 Generate the variable a_discipline_relinquishdummy which is the dummy data
````

generate a_discipline_relinquishdummy = 1
replace a_discipline_relinquishdummy = 0 if a_discipline_relinquish == "No"
replace a_discipline_relinquishdummy = . if a_discipline_relinquish == "NA"
replace a_discipline_relinquishdummy = . if a_discipline_relinquish == "Indefinite"
replace a_discipline_relinquishdummy = . if a_discipline_relinquish == "indefinite"
````
## 10.3 Find all the elements that have special character
````
generate special_character = regexm(a_discipline_relinquish, "[^,.0-9-YesNoNA]")

drop special_character
````
# 11. From data a_letter
## 11.1 Generate the variable a_letternumeric which is the numeric data.
````
generate a_letternumeric1 = real(regexs(1)) if regexm(subinstr(a_letter, ",", "", .), "[0-9]+ - ([0-9]+(\.[0-9]+)?)")  

generate a_letternumeric2 = real(regexs(1)) if regexm(subinstr(a_letter, ",", "", .), "^([0-9]+(\.[0-9]+)?)$")

generate a_letternumeric3 = .
replace a_letternumeric3 = 0 if a_letter == "No"

generate a_letternumeric = a_letternumeric1
replace a_letternumeric = a_letternumeric2 if a_letternumeric2 != .
replace a_letternumeric = a_letternumeric3 if a_letternumeric3 != .
format a_letternumeric %9.2f
drop a_letternumeric1 a_letternumeric2 a_letternumeric3
````
## 11.2 Generate the variable a_letterdummy which is the dummy data
````
generate a_letterdummy = 1
replace a_letterdummy = 0 if a_letter == "No"
replace a_letterdummy = . if a_letter == "NA"
replace a_letterdummy = . if a_letter == "Indefinite"
replace a_letterdummy = . if a_letter == "indefinite"
````
## 11.3 Find all the elements that have special character
````
generate special_character = regexm(a_letter, "[^,.0-9-YesNoNA]")

drop special_character
````

# 12. From data a_practice_restriction
## 12.1 Generate the variable a_practice_restrictionnumeric which is the numeric data.
````
generate a_practice_restrictionnumeric1 = real(regexs(1)) if regexm(subinstr(a_practice_restriction, ",", "", .), "[0-9]+ - ([0-9]+(\.[0-9]+)?)")  

generate a_practice_restrictionnumeric2 = real(regexs(1)) if regexm(subinstr(a_practice_restriction, ",", "", .), "^([0-9]+(\.[0-9]+)?)$")

generate a_practice_restrictionnumeric3 = .
replace a_practice_restrictionnumeric3 = 0 if a_practice_restriction == "No"

generate a_practice_restrictionnumeric = a_practice_restrictionnumeric1
replace a_practice_restrictionnumeric = a_practice_restrictionnumeric2 if a_practice_restrictionnumeric2 != .
replace a_practice_restrictionnumeric = a_practice_restrictionnumeric3 if a_practice_restrictionnumeric3 != .
format a_practice_restrictionnumeric %9.2f
drop a_practice_restrictionnumeric1 a_practice_restrictionnumeric2 a_practice_restrictionnumeric3

````
## 12.2 Generate the variable a_practice_restrictiondummy which is the dummy data
````
generate a_practice_restrictiondummy = 1
replace a_practice_restrictiondummy = 0 if a_practice_restriction == "No"
replace a_practice_restrictiondummy = . if a_practice_restriction == "NA"
replace a_practice_restrictiondummy = . if a_practice_restriction == "Indefinite"
replace a_practice_restrictiondummy = . if a_practice_restriction == "indefinite"
````
## 12.3 Find all the elements that have special character
````
generate special_character = regexm(a_practice_restriction, "[^,.0-9-YesNoNA]")  

drop special_character
````
# 13. From data a_suspension
## 13.1 Generate the variable a_suspensionnumeric which is the numeric data.
````
generate a_suspensionnumeric1 = real(regexs(1)) if regexm(subinstr(a_suspension, ",", "", .), "[0-9]+ - ([0-9]+(\.[0-9]+)?)")  

generate a_suspensionnumeric2 = real(regexs(1)) if regexm(subinstr(a_suspension, ",", "", .), "^([0-9]+(\.[0-9]+)?)$")

generate a_suspensionnumeric3 = .
replace a_suspensionnumeric3 = 0 if a_suspension == "No"

generate a_suspensionnumeric = a_suspensionnumeric1
replace a_suspensionnumeric = a_suspensionnumeric2 if a_suspensionnumeric2 != .
replace a_suspensionnumeric = a_suspensionnumeric3 if a_suspensionnumeric3 != .
format a_suspensionnumeric %9.2f
drop a_suspensionnumeric1 a_suspensionnumeric2 a_suspensionnumeric3
````
## 13.2 Generate the variable a_suspensiondummy which is the dummy data
````
generate a_suspensiondummy = 1
replace a_suspensiondummy = 0 if a_suspension == "No"
replace a_suspensiondummy = . if a_suspension == "NA"
replace a_suspensiondummy = . if a_suspension == "Indefinite"
replace a_suspensiondummy = . if a_suspension == "indefinite"
````
## 13.3 Find all the elements that have special character
````
generate special_character = regexm(a_suspension, "[^,.0-9-YesNoNA]")

drop special_character
````
# 14. From data a_revoked
## 14.1 Generate the variable a_revokednumeric which is the numeric data.
````
generate a_revokednumeric1 = real(regexs(1)) if regexm(subinstr(a_revoked, ",", "", .), "[0-9]+ - ([0-9]+(\.[0-9]+)?)")  

generate a_revokednumeric2 = real(regexs(1)) if regexm(subinstr(a_revoked, ",", "", .), "^([0-9]+(\.[0-9]+)?)$")

generate a_revokednumeric3 = .
replace a_revokednumeric3 = 0 if a_revoked == "No"

generate a_revokednumeric = a_revokednumeric1
replace a_revokednumeric = a_revokednumeric2 if a_revokednumeric2 != .
replace a_revokednumeric = a_revokednumeric3 if a_revokednumeric3 != .
format a_revokednumeric %9.2f
drop a_revokednumeric1 a_revokednumeric2 a_revokednumeric3
````
## 14.2 Generate the variable a_revokeddummy which is the dummy data
````
generate a_revokeddummy = 1
replace a_revokeddummy = 0 if a_revoked == "No"
replace a_revokeddummy = . if a_revoked == "NA"
replace a_revokeddummy = . if a_revoked == "Indefinite"
replace a_revokeddummy = . if a_revoked == "indefinite"
````
## 14.3 Find all the elements that have special character
````
generate special_character = regexm(a_revoked, "[^,.0-9-YesNoNA]")

drop special_character
````
# 15. From data a_priviledge
## 15.1 Generate the variable a_priviledgenumeric which is the numeric data.
````
generate a_priviledgenumeric1 = real(regexs(1)) if regexm(subinstr(a_priviledge, ",", "", .), "[0-9]+ - ([0-9]+(\.[0-9]+)?)")  

generate a_priviledgenumeric2 = real(regexs(1)) if regexm(subinstr(a_priviledge, ",", "", .), "^([0-9]+(\.[0-9]+)?)$")

generate a_priviledgenumeric3 = .
replace a_priviledgenumeric3 = 0 if a_priviledge == "No"

generate a_priviledgenumeric = a_priviledgenumeric1
replace a_priviledgenumeric = a_priviledgenumeric2 if a_priviledgenumeric2 != .
replace a_priviledgenumeric = a_priviledgenumeric3 if a_priviledgenumeric3 != .
format a_priviledgenumeric %9.2f
drop a_priviledgenumeric1 a_priviledgenumeric2 a_priviledgenumeric3
````
## 15.2 Generate the variable a_priviledgedummy which is the dummy data
````
generate a_priviledgedummy = 1
replace a_priviledgedummy = 0 if a_priviledge == "No"
replace a_priviledgedummy = . if a_priviledge == "NA"
replace a_priviledgedummy = . if a_priviledge == "Indefinite"
replace a_priviledgedummy = . if a_priviledge == "indefinite"
````
## 15.3 Find all the elements that have special character
````
generate special_character = regexm(a_priviledge, "[^,.0-9-YesNoNA]")

drop special_character
````

# 16 label every variable
````
label variable a_cost "the numeric variable of paycosts"

. label variable a_anycost "the dummy variable of paycosts"

. label variable a_finenumeric "the numeric variable of a_fine"

. label variable a_cost "the numeric variable of a_paycosts"

. label variable a_anycost "the dummy variable of a_paycosts"

. label variable a_finedummy "the dummy varibale of a_fine"

. label variable a_reprimandnumeric "the numeric variable of a_reprimand"

. label variable a_reprimanddummy "the dummy variable of a_reprimand"

. label variable a_supervisionnumeric "the numeric variable of supervision"

. label variable a_supervisiondummy "dummy variable for a_supervision"

. label variable a_supervisionnumeric "numeric variable of a_supervision"

. label variable a_reprimanddummy "dummy variable of a_reprimand"

. label variable a_reprimandnumeric "numeric variable of a_reprimand"

. label variable a_finedummy "dummy varibale of a_fine"

. label variable a_finenumeric "numeric variable of a_fine"

. label variable a_anycost "dummy variable of a_paycosts"

. label variable a_cost "numeric variable of a_paycosts"

. label variable a_assessmentnumeric "numeric variable"

. label variable a_assessmentnumeric "numeric variable for a_assessment"

. label variable a_assessmentdummy "dummy variable for a_assessment"

. label variable a_communitynumeric "numeric variable for"

. label variable a_communitynumeric "numeric variable for a_community"

. label variable a_communitydummy "dummy variable for a_community"

. label variable a_probationnumeric "numeric variable for a_probation"

. label variable a_probationdummy "dummy variable for a_probation"

. label variable a_educationnumeric "numeric variable for a_education"

. label variable a_educationdummy "dummy variable for a_education"

. label variable a_voluntary_relinquishnumeric "numeric variable for"

. label variable a_voluntary_relinquishnumeric "numeric variable for a_voluntary_relinquish"

. label variable a_voluntary_relinquishdummy "dummy variable for a_voluntary_relinquish"

. label variable a_discipline_relinquishnumeric "numeric variable for a_discipline_relinquish"

. label variable a_discipline_relinquishdummy "dummy variable for a_discipline_relinquish"

. label variable a_letternumeric "numeric variable for a_letter"

. label variable a_letterdummy "dummy variable a_letter"

. label variable a_practice_restrictionnumeric "numeric variable for a_practice_restriction"

. label variable a_practice_restrictiondummy "dummy variable for a_practice_restriction"

. label variable a_suspensionnumeric "numeric variable for a_suspension"

. label variable a_suspensiondummy "dummy variable for a_suspension"

. label variable a_revokednumeric "numeric variable for a_revoked"

. label variable a_revokeddummy "dummy variable for a_revoked"

. label variable a_priviledgenumeric "numeric variable for a_priviledge"

. label variable a_priviledgedummy "dummy variable for a_priviledge"
````
