from datetime import datetime
import time
from urllib.request import urlopen
from bs4 import BeautifulSoup
from urllib.request import Request, urlopen
import ezodf
import time

spread=ezodf.opendoc('file.ods')
sheet1=spread.sheets[0]
sheet1.reset(size=(50,50))
i=1

while True:
    dt=datetime.now()
    if dt.hour==8 or dt.hour==9 or dt.hour==10 or dt.hour==11 or dt.hour==12\
       or dt.hour==13 or dt.hour==14 or dt.hour==15 or dt.hour==16 or dt.hour==17\
       or dt.hour==18 or dt.hour==19 or dt.hour==20:
        if (dt.minute==0 and dt.second==0 and dt.microsecond==0):

            def getData(i):

                #Get Data IG
                
                html = urlopen("website, example: https://www.ig.com/es/indices/mercado-indices/espana-35")
                soup = BeautifulSoup(html,features='html.parser')
                percentageIG =soup.find_all('span',class_='price-ticket__percent')
                directionIG = soup.find_all('strong')
                percentageIG1=percentageIG[0]
                percentageIG2=str(percentageIG1)
                percentageIG3=percentageIG2[36:38]
                directionIG1=directionIG[0]
                directionIG2=str(directionIG1)
                directionIG3=directionIG2[8:13]
                if directionIG3=='largo':
                    percentageIG4=percentageIG3
                else:
                    percentageIG4=100-(int(percentageIG3))

                #Get Data Plus
                    
                req = Request('https://www.plus500.es/Instruments/IBX?searchTerm=espa%C3%B1a', headers={'User-Agent': 'Mozilla/5.0'})
                html1 =urlopen(req)
                soup1 = BeautifulSoup(html1,features='html.parser')
                percentagePlus = str(soup1.find_all('script'))
                percentagePlus1 = percentagePlus[3668:3670]
                pricePlus = percentagePlus[3308:3312]

                #Salida de datos

                celdaFecha='A'+str(i)
                celdaHora='B'+str(i)
                celdaIg='C'+str(i)
                celdaPlus='D'+str(i)
                celdaPrice='E'+str(i)

                sheet1[celdaFecha].set_value(time.strftime('%x'))
                sheet1[celdaHora].set_value(time.strftime('%X'))
                sheet1[celdaIg].set_value(percentageIG4)
                sheet1[celdaPlus].set_value(percentagePlus1)
                sheet1[celdaPrice].set_value(pricePlus)
                
                i=i+1

                spread.save()
               
                print(time.strftime('%x'),'',end='')
                print(time.strftime('%X'),':',sep='')
                print('IG:',percentageIG4)
                print('Plus500:',percentagePlus1)
                print('Price:',pricePlus)
                
          
            getData(i)
            time.sleep(3000)
            i=i+1
