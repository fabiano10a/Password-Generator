# Password-Generator

import random
from datetime import datetime
import string as str

def password(panjang):
    karakter = str.ascii_letters + str.digits + str.punctuation
    password = ''.join(random.choice(karakter) for _ in range(panjang))
    return password

while True:
    try:
        panjang = int(input("Berapa karakter yang di butuhkan: "))
    
        if panjang == 0:
            print("terima kasih")
            break
    
        password = password(panjang)
        print(f"Ini Password Kamu: {password}")

        nama_file = "password_{}.txt".format(datetime.now().strftime("%Y%m%d_%H%M%S"))

        with open(nama_file, "w") as file:
            file.write("Ini Password Kamu:\n")
            file.write(password)

        print(f"Password Kamu Disimpan Di: {nama_file}")
     
    except ValueError:
        print("Masukan angka yang valid")
