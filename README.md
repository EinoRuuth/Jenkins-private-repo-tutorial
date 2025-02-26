# Jenkins-private-repo-tutorial
## kuinka tehdä ssh avaimet
ekana katso että services kohdassa on opensshagen päällä
<img height="100" src="https://media.discordapp.net/attachments/1143805627718713375/1344335041500545134/Screenshot_155.png?ex=67c08912&is=67bf3792&hm=9c312ad119ad7276e13d36da7973bf33adfd615dca931bf90d5554e3f9c0c9b8&=&format=webp&quality=lossless&width=609&height=92">

avaa cmd katso mikä on home folderisi (``yleensä C:\Users\"user"``)<br />
mene .ssh kansioon (``jos ei ole, tee semmoinen home foleriin``)<br />
Kun olet cmd;ssä .ssh kansiossa runaa komento <br />
``$ ssh-keygen``

laita filen nimeksi mikä vaan (``vaikka jenkins``)<br />
password jättää tyhjäksi mutta jos haluaa voi siihen laittaa jotain<br />
sitten .ssh kansioon pitäisi olla tullut kaksi tiedostoa "filenimi" sekä "filenimi".pub (``filenimi on nimi jonka annouit kun teit avaimen nimillä``)

<img height="60" src="https://media.discordapp.net/attachments/1143805627718713375/1344335041710395456/Screenshot_156.png?ex=67c08912&is=67bf3792&hm=3e1282b00d856b86efdf60ddfcf319a84e0acf3b778ba616bec325cf64d33d5e&=&format=webp&quality=lossless&width=500&height=51">

## ssh avain githubin puolella
avaa github seilaimessa ja mene asetuksiin jossa on ssh and gpg keys

<img height="150" src="https://media.discordapp.net/attachments/1143805627718713375/1344335042029027399/Screenshot_157.png?ex=67c08912&is=67bf3792&hm=3bb79dca4edcd3b35e44c8edc8adc0a7108e4f2b85a92f972dd5a8a542a294aa&=&format=webp&quality=lossless&width=250&height=234">

klikkaa "new ssh key"<br />
tälle voit antaa mikä vaan title (``esim jenkins``)<br />
key type on authentiaction key<br />
sitten avaa "filenimi".pub avain tiedosto vaikka notepadissa<br />
ja key kohtaan kopiot sen mitä "filenimi".pub file sisältää<br />
ja sitten paina lisää nappia

## ssh avain jenkinsin puolella
avaa Jenkins<br />
configure Jenkins ja security kohdasta credentials<br />
klikkaa global kohtaa joka näkyy alla olevassa kuvassa

<img height="100" src="https://media.discordapp.net/attachments/1143805627718713375/1344335042545193084/Screenshot_159.png?ex=67c08912&is=67bf3792&hm=63dccaf8a8c949fa89e816463be36ebcd23b4fc5dd039b096aef86dc820b613a&=&format=webp&quality=lossless&width=380&height=116">

klikkaa add credentials<br />
ja ylhäältä valitset "ssh username with private key"<br />
ID saa valita itse mutta muista se<br />
username kohtaan laittaa GitHub usernamen<br />
sitten checkkaa enter key directly ja add (``kuva``)

<img height="100" src="https://media.discordapp.net/attachments/1143805627718713375/1344335042788458638/Screenshot_160.png?ex=67c08912&is=67bf3792&hm=1967ef6c9917be593a9b496796b7014b179605f02f12556aa76e6a5b92630fe5&=&format=webp&quality=lossless&width=1240&height=138">

kopio alempaan kenttään mikä tuli esille sinun "filenimi" tiedoston sisältö (``eli se toinen .ssh kansion tiedosto``)<br />
laita passphrase kohtaan password jos laitoit semmoisen keygenissä (``jos jätit tehjäksi salasanan nii tämäkin on tyhjä``)<br />
sitten create

nyt on ssh avaimet hoidettu

## ssh avainten käyttö
kun teet Jenkins jobin jossa on private githubi repo käytössä niin sinun pitää käyttää ssh linkkiä jonka saat kuvan mukaan

<img height="150" src="https://media.discordapp.net/attachments/1143805627718713375/1344335042310176778/Screenshot_158.png?ex=67c08912&is=67bf3792&hm=e85b82772d4960b2aea42f3d3924350084c83145be5c40ea0141004098973984&=&format=webp&quality=lossless&width=361&height=296">

Jenkins file pitää muuttaa myös<br />
eli git kohtaan pitää lisätä credentialsId joka on id jonka annoit sinun Jenkins credentials

<img height="100" src="https://media.discordapp.net/attachments/1143805627718713375/1344335043228602378/Screenshot_161.png?ex=67c08912&is=67bf3792&hm=a14e3d83f218f2f703b78618eb874bd7707b5975dda866e7866217051931bec7&=&format=webp&quality=lossless&width=461&height=49">
jos unohdit minkä annoit se näkyy Jenkins credentials kohdassa
<img height="100" src="https://media.discordapp.net/attachments/1143805627718713375/1344335043501363240/Screenshot_162.png?ex=67c08912&is=67bf3792&hm=4021a745df268f969271abb6c0ca3e73bade180c20f1f37449e4eb71ccbf8955&=&format=webp&quality=lossless&width=1015&height=133">

ja homma on sitten hoidettu.<br />
happy jenkinsin
