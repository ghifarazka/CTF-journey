---
description: participated as insidious_hex
---

# OSCCTF

## Cryptography

### RepeatMe (100 pts)

Diberikan file chall.txt yang berisi teks yang terlihat seperti di-encode dengan base64. Menggunakan bantuan CyberChef, teks tersebut di-decode menggunakan base64 dan base32 berulang kali sehingga flag-nya didapatkan.

Flag: OSC2022{repeat\_the\_base}

### Shamir (200 pts)

Diberikan file chall.py dan outputnya yaitu output.txt. Di sini, kita bisa melihat bahwa soalnya kurang lebih sama dengan soal RSA pada umumnya, hanya saja phi dikalikan dengan bilangan random k.&#x20;

Karena batas angka random tersebut tidak sebanding dengan jumlah byte p dan q (1024), maka saya mengira bahwa hasil kali phi dan k tidak terlalu berbeda jauh. Jika benar tidak berbeda jauh, maka \[d\*e mod(kphi) = 1] hasilnya akan sama saja dengan \[d\*e mod(phi) = 1]. Berikut adalah kode solvernya.

```python
c= 7122175960852496938475393339139207199088670246253603618307801787286894108828782105596039197147169650719301776107664229881034338822166454707727326561182204630625153673881465984372829614190797411662714153592210095613132089565075110026594781421785171659101583969664621807242453750331798043357485010977272403583369552781164422513721643016757410051923946703417694390707321503534366693343134050177450499566649510997468997768983671699194417651249278316132917308374923522476942815196034928371196099780886463076498847229545961662332931942581031454817423688325698364342987746470512053086887501044086549338805486558431128736066
n= 14271578418243991182948053790020939604709913291240698269722057521898121666257201008378155951082215094743985416112814155416041637109048209896498049350850398863230921222625695245595648478712468316028827291570002981943598195360594449192095310767925103828018503658506789429532794282804715424285580728595876813137257367967214214187712005954474808189735398872202288587176457554475557547935956191021081222387113719102264032090294484281147553053650496094646634072222703650863210301277293405637971348347271180618913368939005306155047399923688312134829227011262152812278285408086835138886519140271337574648445256272539866945829
e= 65537

phi = 62835455821362858004517774398316888530647913562616956289318938795810695946114686391275144069834668015444902501631122488285448487888377835599404350150197272927683792670201720609508857623639506147030009150212950278770326313652277965129502628808901929003920094282974241222143147998971905502996055161264134344207199700769472486805803536134414274484629896308756749764159247099887628072711931757517360938478167529596745710365075700924571611085399756537841907692858069984319936297798206794309497405564832050518315866418185301146419880668003285249207576065806438675563011065708510182559803540975739216355263152797670111445668145515195530756160

d = pow(e,-1,phi)
m = pow(c,d,n)

hex_m = hex(m)[2:]
plain_m = bytes.fromhex(hex_m).decode('ascii','ignore')

print(f'hex_m = {hex_m}')
print(f'plain_m = {plain_m}')
```

Flag: OSC2022{rsa\_with\_big\_k\_really???}

## Web Exploitation

### Inspect Me (100 pts)

Diberikan link menuju sebuah website yaitu [http://139.59.117.189:5001/](http://139.59.117.189:5001/). Pada website tersebut, saya melakukan inspect dan flag ditemukan.

Flag: OSC2022{CLA$SI1111C\_ch4l1enGE\_On\_W3BBB}

### Login (100 pts)

Diberikan link menuju sebuah website yaitu [http://139.59.117.189:5002/](http://139.59.117.189:5002/). Pada website tersebut, ada form login dan hint kode SQL yang ada dibaliknya. Tentu cara menyelesaikan soal ini adalah dengan melakukan SQL injection. Saya memasukkan ' OR '1'='1 ke bagian username dan password. Login berhasil dan flag didapatkan.

Flag: OSC2022{SQLi\_goeS\_BrrRrRR!!!}\