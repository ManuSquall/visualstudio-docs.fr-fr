---
title: "IDiaAddressMap::set_addressMap | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaAddressMap::set_addressMap (méthode)"
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaAddressMap::set_addressMap
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Fournit une configuration d'adresse aux traductions de disposition des images de stockage.  
  
## Syntaxe  
  
```cpp#  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### Paramètres  
 `cbData`  
 \[in\]  le nombre d'éléments dans le paramètre d' `data` .  
  
 `data[]`  
 \[in\]  Un tableau de structures de [DiaAddressMapEntry, structure](../../debugger/debug-interface-access/diaaddressmapentry.md) qui définissent le mappage de traduction.  
  
 `imagetoSymbols`  
 \[in\]  `TRUE` si le paramètre d' `data` définit une carte de la nouvelle disposition des images à la disposition d'origine \(comme indiqué par les symboles de débogage\).  `FALSE` si `data` est une carte à la nouvelle disposition d'image prise de la disposition d'origine.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Généralement, le diamètre extrait des cartes de translation d'adresses du fichier de base de données du programme \(.pdb\).  Si ces valeurs sont absentes, la méthode d' [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) est appelée deux fois, avec le jeu de paramètres d' `imagetoSymbols` à `TRUE` et une fois avec le jeu de paramètres d' `imagetoSymbols` à `FALSE`.  Les traductions de configuration d'adresse ne peuvent pas être activées à l'aide de la méthode d' [IDiaAddressMap::put\_addressMapEnabled](../Topic/IDiaAddressMap::put_addressMapEnabled.md) à moins que les deux cartes de traduction soient fournies.  
  
## Voir aussi  
 [DiaAddressMapEntry, structure](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put\_addressMapEnabled](../Topic/IDiaAddressMap::put_addressMapEnabled.md)   
 [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)