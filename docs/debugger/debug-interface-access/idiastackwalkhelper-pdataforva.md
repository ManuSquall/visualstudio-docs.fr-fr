---
title: "IDiaStackWalkHelper::pdataForVA | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::pdataByVA (méthode)"
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Retourne le bloc de données de PDATA associé à l'adresse virtuelle.  
  
## Syntaxe  
  
```cpp#  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### Paramètres  
 `va`  
 \[in\]  Spécifie l'adresse virtuelle de données pour obtenir.  
  
 `cbData`  
 \[in\]  la taille des données en octets à obtenir.  
  
 `pcbData`  
 \[out\]  Retourne la grandeur réelle de la donnée en octets qui a été obtenu.  
  
 `pbData`  
 \[in, out\]  Une mémoire tampon qui est terminée avec les données demandées.  La valeur ne peut pas être `NULL`.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` s'il n'y a aucun PDATA pour l'adresse spécifiée.  Sinon, retourne un code d'erreur.  
  
## Notes  
 Le PDATA \(la section nommée « .pdata »\) d'un module \(compiland\) contient des informations sur la gestion des exceptions pour les fonctions.  
  
 L'appelant est le nombre données de réalisation être retournée pour que l'appelant n'avez pas besoin de demander la quantité données de réalisation disponible.  Par conséquent, il est acceptable pour une implémentation de cette méthode retourne une erreur si le paramètre d' `pbData` est `NULL`.  
  
## Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)