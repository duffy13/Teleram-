
import requests

def send_msg(text):
    token = "1630972311:AAERHPGRwgmHkGmGVSbHCNFJAaF8cfZVr0o"
    chat_id = "662955399"
    url_req = "https://api.telegram.org/bot"+ token + "/sendmessage" + "?chat_id=" + chat_id + "&text=" + text
    results = requests.get(url_req)
    return results.json()

send_msg("good job")