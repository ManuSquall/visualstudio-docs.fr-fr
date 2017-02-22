---
title: "IDiaEnumLineNumbers::get__NewEnum | Microsoft Docs"
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
  - "IDiaEnumLineNumbers::get__NewEnum (méthode)"
ms.assetid: 8b15f76b-a431-4f60-8bed-3206256b0d10
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumLineNumbers::get__NewEnum
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
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)