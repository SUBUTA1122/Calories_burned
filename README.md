# Calories_burned
name=input('名前:')
age=int(input('年齢:'))
weight=float(input('体重(kg):'))
hight=float(input('身長(cm):'))
sex=input('性別(men or women):')

if sex == 'men':
    constant=72.46
else:
    constant=70.49
    
#BSA:body surface area (cm**2)
#BSA is calculated in the DuBois.

BSA=weight**0.425*hight**0.725*constant
BSAm=BSA/10000 #change cm**2 to m**2 for the BSA.

#BMR=basal metabolic rate
if sex=='men':
    if age==1:BMR=56.8
    elif age==2:BMR=57.2
    elif age==3:BMR=56.8
    elif age==4:BMR=54.7
    elif age==5:BMR=52.3
    elif age==6:BMR=51.2
    elif age==7:BMR=49.4
    elif age==8:BMR=47.6
    elif age==9:BMR=45.8
    elif age==10:BMR=44.6
    elif age==11:BMR=43.7
    elif age==12:BMR=42.9
    elif age==13:BMR=41.9
    elif age==14:BMR=41.0
    elif age==15:BMR=40.2
    elif age==16:BMR=39.5
    elif age==17:BMR=38.8
    elif age==18:BMR=38.2
    elif age==19:BMR=37.4
    elif age==20:BMR=36.9
    elif age>20 and age<30:BMR=36.2
    elif age>=30 and age<40:BMR=35.3
    elif age>=40 and age<50:BMR=34.4
    elif age>=50 and age<60:BMR=33.4
    elif age>=60 and age<70:BMR=32.6
    elif age>=70 and age<80:BMR=31.2
    elif age>=80:BMR=29.9

else:
    if age==1:BMR=56.2
    elif age==2:BMR=56.4
    elif age==3:BMR=55.4
    elif age==4:BMR=52.5
    elif age==5:BMR=49.2
    elif age==6:BMR=47.9
    elif age==7:BMR=46.0
    elif age==8:BMR=44.6
    elif age==9:BMR=43.2
    elif age==10:BMR=42.5
    elif age==11:BMR=41.6
    elif age==12:BMR=40.7
    elif age==13:BMR=39.7
    elif age==14:BMR=38.4
    elif age==15:BMR=36.8
    elif age==16:BMR=35.6
    elif age==17:BMR=34.8
    elif age==18:BMR=34.4
    elif age==19:BMR=33.9
    elif age==20:BMR=33.5
    elif age>20 and age<30:BMR=33.1
    elif age>=30 and age<40:BMR=32.1
    elif age>=40 and age<50:BMR=31.5
    elif age>=50 and age<60:BMR=31.0
    elif age>=60 and age<70:BMR=30.5
    elif age>=70 and age<80:BMR=30.0
    elif age>=80:BMR=29.7
        
BMRday=BMR*BSAm*24 #Calculate basal metabolic volume of a day.
BMRhour=BMRday/24

#Calculate exercise intensity in Karvonen Formula.
#EI=exercise intensity
time=float(input('活動の時間(分):'))
actPR=int(input('活動中の心拍数/分:'))
restPR=int(input('安静時の心拍数/分:'))
maxPR=220-age
EI=(actPR-restPR)/(maxPR-restPR)*100
EIMETs=EI/10
hour=time/60
BMRtime=BMRhour*hour

#calculate calories burned of act times(mets only).
Simplekcal=EIMETs*hour*weight*1.05
#RMR:relative metabolic rate
#rest time calories burned is METs 1.
#CB=calories burned
rest_timeCB=1*hour*weight*1.05
RMR=(Simplekcal-rest_timeCB)/BMRtime
CBkcal=RMR*hour*weight
print(name,'さんが',time,'分の活動（',EIMETs,'METs）を行うと',CBkcal,'kcal消費される')
