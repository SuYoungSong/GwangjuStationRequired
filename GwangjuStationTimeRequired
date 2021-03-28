import requests
import json

# 역 이름을 (int)ID로 변경
def ChangeStationName2Num(StationName):
    StationCode = 0
    if StationName == "평동역":
        StationCode = 1
    elif StationName == "도산역":
        StationCode = 2
    elif StationName == "광주송정역":
        StationCode = 3
    elif StationName == "송정공원역":
        StationCode = 4
    elif StationName == "공항역":
        StationCode = 5
    elif StationName == "김대중컨벤션센터역":
        StationCode = 6
    elif StationName == "상무역":
        StationCode = 7
    elif StationName == "운천역":
        StationCode = 8
    elif StationName == "쌍촌역":
        StationCode = 9
    elif StationName == "화정역":
        StationCode = 10
    elif StationName == "농성역":
        StationCode = 11
    elif StationName == "돌고개역":
        StationCode = 12
    elif StationName == "양동시장역":
        StationCode = 13
    elif StationName == "금남로5가역":
        StationCode = 14
    elif StationName == "금남로4가역":
        StationCode = 15
    elif StationName == "문화전당역":
        StationCode = 16
    elif StationName == "남광주역":
        StationCode = 17
    elif StationName == "학동증심사입구역":
        StationCode = 18
    elif StationName == "소태역":
        StationCode = 19
    elif StationName == "녹동역":
        StationCode = 20
    
    if StationName == 0:
        print("역 이름이 잘못 입력되었습니다.")
    return StationCode


# 도착시간 분단위를 초단위로 변경
def TimeMin2Sec(StationTime):
    Minute = int(StationTime)
    MinSec = "ERROR"

    if StationTime-Minute == 0:
        MinSec = str(Minute) + "분"
    else:
        Second = int(((StationTime - Minute) * 10) * 6)
        MinSec = str(Minute) + "분" + str(Second) + "초" 
    
    return MinSec

# 메뉴 보여주기
def printMenu():
    print("-------------------------------------------------------")
    print("1.역이름 확인하기")
    print("2.소요시간 확인하기")
    print("3.종료")
    print("-------------------------------------------------------")

#1번메뉴 / 역 이름 Print
def StationNameInfo():
    print("평동역 - 도산역 - 광주송정역 - 공항역 - 김대중컨벤션센터역 - 상무역 - 운천역 - 쌍촌역 - 화정역 - 농성역 - 돌고개역 - 양동시장역 - 금남로5가역 - 금남로4가역 - 문화전당역 - 남광주역 - 학동증심사입구역 - 소태역 - 녹동역")

#2번메뉴 / 소요시간 확인하기
def StationRequired():
    userInputStartName = input("출발역을 입력해주세요:")
    station_id = ChangeStationName2Num(userInputStartName)

    userInputEndName = input("도착역을 입력해주세요:")
    endStaionNum = ChangeStationName2Num(userInputEndName)
    stationJsonUrl = "http://www.grtc.co.kr/subway/openapi/StationTimeInformation.do?rbsIdx=317&doctype=json" +"&station_id="+ str(station_id)
    stationJson = requests.get(stationJsonUrl).content
    stationJson = json.loads(stationJson)
    
    for station in stationJson:
        if station["start_station_id"] == station_id:
            if station["end_station_id"] == endStaionNum:
                print(station["start_station_name"] + "에서 " + station["end_station_name"] +"까지 예상소요시간은 " + TimeMin2Sec(station["station_time"]) +" 입니다")

printMenu()

while(1):
    userInputSelectMenu = input("=>메뉴를 선택하세요:")
    if userInputSelectMenu == "1":
        StationNameInfo()
    elif userInputSelectMenu == "2":
        StationRequired()
    elif userInputSelectMenu == "3":
        break
    else:
        print("다시 입력하세요.")

