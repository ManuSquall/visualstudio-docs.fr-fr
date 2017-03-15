---
title: "IDiaEnumFrameData::get__NewEnum | Microsoft Docs"
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
  - "IDiaEnumFrameData::get__NewEnum (méthode)"
ms.assetid: f5fe0279-0549-4af5-8f89-bcb535fc5809
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumFrameData::get__NewEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère la version d' <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> de cet énumérateur.  
  
## Syntaxe  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### Paramètres  
 pRetVal  
 \[out\]  Retourne l'interface d' `IUnknown` qui représente la version d' <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> de cet énumérateur.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)