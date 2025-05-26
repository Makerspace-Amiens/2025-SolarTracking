---
layout: default
nav_order: 4
parent: Partie Electronique
title: BuckBoost
---

[Retour](partie_électronique.md)


<h1>Buck Boost</h1>

On pense prendre un MT3608 ou XL6009. 

Un module MT3608 peut convenir, mais il est limité à 2A max. Mais si on veut plus de marge, un XL6009 ou LM2577 serait plus robuste. 

MT https://fr.aliexpress.com/item/1005006519538977.html?UTABTest=aliabtest112699_10027&src=google&src=google&albch=shopping&acnt=248-630-5778&slnk=&plac=&mtctp=&albbt=Google_7_shopping&gclsrc=aw.ds&albagn=888888&ds_e_adid=729376560873&ds_e_matchtype=search&ds_e_device=c&ds_e_network=g&ds_e_product_group_id=297546631617&ds_e_product_id=fr1005006519538977&ds_e_product_merchant_id=5326692037&ds_e_product_country=FR&ds_e_product_language=fr&ds_e_product_channel=online&ds_e_product_store_id=&ds_url_v=2&albcp=22139907784&albag=176614257307&isSmbAutoCall=false&needSmbHouyi=false&gad_source=1&gclid=Cj0KCQjw16O_BhDNARIsAC3i2GBF4TvjZh4zYBEAFmXvYxGzXzyLjNheM2LZVQ_NzELPuYoqCy9NktkaApUYEALw_wcB&aff_fcid=c03c0ac62ac14728a4689d4d3658b3a6-1743373986238-08008-UneMJZVf&aff_fsk=UneMJZVf&aff_platform=aaf&sk=UneMJZVf&aff_trace_key=c03c0ac62ac14728a4689d4d3658b3a6-1743373986238-08008-UneMJZVf&terminal_id=76c882c57c894ee782fe70cc949022fd&OLP=1103400108_f_group2&o_s_id=1103400108&afSmartRedirect=n&gatewayAdapt=glo2fra 

XL https://www.amazon.fr/Adaptateur-dAlimentation-dEnergie-Affichage-Num%C3%A9rique/dp/B075JQTPX6/ref=asc_df_B075JQTPX6?mcid=de9905972c2036ee8da1c5b2c78206c3&tag=googshopfr-21&linkCode=df0&hvadid=701535511897&hvpos=&hvnetw=g&hvrand=3894480706799083848&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9109572&hvtargid=pla-608442334226&psc=1&gad_source=1 

 

Ou même un LVBOOST à voir avec les valeurs du SOL3W: 

https://www.gotronic.fr/art-booster-2-2-a-5-v-lvboost-14352.htm  

Ressource: https://www.dimensionengineering.com/LVBoost.pdf  

Le LVBoost peut utiliser des tensions aussi faibles que 0,5 Vcc pour les convertir en tensions plus élevées et utilisables dans la plage de 2,2 à 5 Vcc. La tension de sortie se règle à l'aide d'un potentiomètre ajustable. 
 
Ne nécessite pas de composants externes. Ses applications sont nombreuses: chargeurs solaires, régulateurs solaires, mini-éoliennes, etc. 

![BUCKboost]("../Partie_électronique/buckboost.webp" width="400")
 
Caractéristiques techniques: 
- Tension d'entrée: 0,5 à 5 Vcc 
- Tension de sortie: 2,2 à 5 Vcc 
- Intensité maxi en entrée: 1,5 A 
- Intensité maxi en sortie: 1,5 A 
- Ondulation typique: 20 mV 
Connectique: fils à souder de 8 cm 
Dimensions: 19 x 10 x 8 mm 
Poids: 3,5 gr

[Retour](partie_électronique.md)