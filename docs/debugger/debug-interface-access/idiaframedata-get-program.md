---
title: "IDiaFrameData::get_program | Microsoft Docs"
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
  - "IDiaFrameData::get_program (méthode)"
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaFrameData::get_program
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait la chaîne de programme qui est utilisée pour calculer le jeu de registres avant l'appel à la fonction active.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### Paramètres  
 `pRetVal`  
 \[out\]  Retourne la chaîne de programme.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`.  Retourne `S_FALSE` si cette propriété n'est pas prise en charge.  Sinon, retourne un code d'erreur.  
  
## Notes  
 La chaîne de programme est une séquence de macros qui est interprétée pour générer le prologue.  Par exemple, un frame de pile typique peut utiliser la chaîne `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`de programme.  le format est notation de polonais inversé, où les opérateurs suivent les opérandes.  `T0` représente une variable temporaire sur la pile.  Cet exemple exécute les étapes suivantes :  
  
1.  Le contenu des mouvements de registre `ebp` à `T0`.  
  
2.  Ajoutez `4` à la valeur dans `T0` pour produire une adresse, récupérez la valeur de cette adresse, et stocker la valeur dans le registre `eip`.  
  
3.  Récupérez la valeur de l'adresse stockée dans `T0` et enregistrez cette valeur dans le registre `ebp`.  
  
4.  ajoutez `8` à la valeur dans `T0` et enregistrez cette valeur dans le registre `esp`.  
  
 Notez que la chaîne de programme est spécifique à le processeur et à l'installation de convention d'appel pour la fonction représentée par le frame de pile actuel.  
  
## Voir aussi  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)