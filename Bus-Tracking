import time
import urllib
from xml.etree.ElementTree import parse
import os

os.chdir("/home/Hoods/pref/Hacking_with_python")

my_lat=41.98062
my_lon=-87.668452
buses=[]
def data_access():
    u=urllib.urlopen('http://ctabustracker.com/bustime/map/getBusesForRoute.jsp?route=22')
    data=u.read()
    f=open('route22.xml','wb')
    f.write(data)
    f.close()



def find_bus():
        doc=parse('route22.xml')
        for bus in doc.findall('bus'):
            lat=float(bus.findtext('lat'))
            if lat>my_lat:
                dir=bus.findtext('d')
                if dir.startswith('North'):
                    bus_id=bus.findtext('id')
                    buses.append(bus_id)
                    print bus_id,dir,lat

def distance(lat1,lat2):
    return 69*abs(lat1-lat2)

def monitor():
    doc=parse('route22.xml')
    for bus in doc.findall('bus'):
        bus_id=bus.findtext('id')
        lat=float(bus.findtext('lat'))
        dis=distance(lat,my_lat)
        print 'ID :', bus_id,'Distance :' , dis ,'Latitude :',lat
    print '*'*60

while True:
    data_access()
    monitor()
    time.sleep(60)


