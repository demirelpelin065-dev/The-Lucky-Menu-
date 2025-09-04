# The-Lucky-Menu-
The Lucky Menu ⭐  Description

import random 


def thePowerOfTwo(x):
    if x>21: #if-sats som kontrollerar om vår input är större än 21
        print("You have bypassed the maximum input-value (21) possible for this function!")
        #begränsa outputet till 2^21 om villkoret är sant
        for i in range(21):
            print(f"2^{i} = {2**i}")
    else:
        for i in range(x):
            print(f"2^{i} = {2**i}")
    print("\n") #tom rad, så att det blir finare struktur i programmet
    

def tarningSpel(omgangar):
    poang_1 = 0
    poang_2 = 0
    mina_kast= []  # Lista för att lagra mina kast
    datorns_kast=[] # Lista för att lagra datorns kast

    for i in range(omgangar):
        print(f"Omgång {i + 1} påbörjas..\n")
        input("Tryck på Enter för att kasta tärningen!")
        slumptal_1 = random.randint(1, 6)
        mina_kast.append(slumptal_1)
        print(f"Du fick {slumptal_1}\n")
        input("Motståndarens tur, tryck på Enter för att fortsätta!")
        slumptal_2 = random.randint(1, 6)
        datorns_kast.append(slumptal_2)
        print(f"Motståndaren fick {slumptal_2}\n")

        if slumptal_1 > slumptal_2:
            print("Du vann omgången!")
            poang_1 += 1
            print(f"Poäng efter denna omgång är {poang_1}-{poang_2} (Du vs Motståndare)")
        elif slumptal_1 < slumptal_2:
            print("Du förlorade omgången!")
            poang_2 += 1
            print(f"Poäng efter denna omgång är {poang_1}-{poang_2} (Du vs Motståndare)")
        else:
            print("Den här omgången är oavgjord!")
            print(f"Poäng efter denna omgång är {poang_1}-{poang_2} (Du vs Motståndare)")

        print("\n")
    print(f"Slutpoäng är {poang_1}-{poang_2} (Du vs Motståndare)")
    if poang_1 > poang_2:
        print("Grattis! Du vann spelet!")
    elif poang_1 < poang_2:
        print("Tyvärr förlorade du spelet. Motståndaren är segrare!")
    else:
        print("Spelet slutade oavgjort!")

    # Beräkna och skriv ut statistik
    medel_kast_1= round(sum(mina_kast) / len(mina_kast), 1) #beräkning av medelvärde
    medel_kast_2= round(sum(datorns_kast) / len(datorns_kast), 1)
    lagsta_kast_1=min(mina_kast)
    lagsta_kast_2=min(datorns_kast)
    hogsta_kast_1=max(mina_kast)
    hogsta_kast_2=max(datorns_kast)
    print(f"\nMedelvärdet av dina kast under alla omgångar: {medel_kast_1}")
    print(f"Medelvärdet av motståndarens kast under alla omgångar: {medel_kast_2} \n")
    print(f"Ditt lägsta kast under någon omgång: {lagsta_kast_1} ")
    print(f"Motståndarens lägsta kast under någon omgång: {lagsta_kast_2} \n")
    print(f"Ditt högsta kast under någon omgång: {hogsta_kast_1}")
    print(f"Motståndarens högsta kast under någon omgång: {hogsta_kast_2}\n")





def gissaSlumptal():
    mindre_sju=0 #boolean-variabel som visar om det tog <=7 forsök eller inte
    antal_forsok = 0
    slumpat_tal = random.randint(1, 100)
    
    while True:
        anvandarens_gissning = int(input("Gissa ett tal mellan 1 och 100: "))
        antal_forsok += 1
        
        if anvandarens_gissning == slumpat_tal:
            print(f"Du gissade rätt på {antal_forsok} försök.")
            if antal_forsok<=7:
                print("Bra jobbat!")
                mindre_sju=1
            else:    
                print("Så många försök borde det inte ta, försök igen.")
            return mindre_sju
        elif anvandarens_gissning < slumpat_tal:
            print("För lågt! Försök igen.")
        else:
            print("För högt! Försök igen.")
        
        



cons_wins=0 # Variabel för att hålla koll på antalet rätt gissningar i rad
while True:
    print("1. thePowerOfTwo()")
    print("2. tarningSpel()")
    print("3. gissaSlumptal()")
    print("4. Close the menu")
    inp=int(input("Välj nogåt av de fyra allternativen  (1 -> 4): "))

   
    if inp==1:
        inp1=int(input("Skriv in ett input för att funkrionen ska starta : "))
        print("\n")
        thePowerOfTwo(inp1)
    
    if inp==2:
        inp2=int(input("Hur många gånger vill du spela? skriv in ett input:"))
        print("\n")
        tarningSpel(inp2)
     

    if inp==3:
       print("\n")
       spela=gissaSlumptal() # =1 om det tog <=7 gissningar, annars =0
       if spela: #om sant (spela=1)
           cons_wins+=1 #vi adderar 1 till cons_wins varje gång vi klarar spelet på <=7 gissningar
       else: #om spela=0
           cons_wins=0 #nollställ om det någon gång tar >7 gissningar

       if cons_wins>=3: #klarar vi spelet 3 eller flera gånger i rad med <=7 gissningar
          print("Du använder bevisligen en bra gissningsstrategi!")    
          
    if inp==4:
        break
    
