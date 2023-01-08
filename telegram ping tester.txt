
import requests
import subprocess
import re

def send_msg(text):
    token = "1630972311:AAERHPGRwgmHkGmGVSbHCNFJAaF8cfZVr0o"
    chat_id = "662955399"
    url_req = "https://api.telegram.org/bot" + token + "/sendmessage" + "?chat_id=" + chat_id + "&text=" + text
    results = requests.get(url_req)
    return results.json()


ip = input("ip : ")


while True:
    try:
        direct_output = subprocess.check_output('ping '+str(ip)+' -n 1', shell=True).decode("utf-8")
        print(direct_output)

        ss = re.search('time=(.*)ms', direct_output).group(1)
        print(ss)

        if int(ss) >= 50:
            send_msg("Your ping is "+str(ss))
    except:
        send_msg("please check your ip or your connection")
        try:
            ss = re.search('time=(.*)ms', direct_output).group(1)
        except:
            continue

