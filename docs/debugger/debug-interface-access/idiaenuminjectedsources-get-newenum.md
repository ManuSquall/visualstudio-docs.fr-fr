---
title: "IDiaEnumInjectedSources::get__NewEnum | Microsoft Docs"
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
  - "IDiaEnumInjectedSources::get__NewEnum (méthode)"
ms.assetid: f56cdcdb-dc71-43c7-82fe-e2500986f5bc
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumInjectedSources::get__NewEnum
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
 \[out, retval\]  Retourne l'interface d' `IUnknown` qui représente la version d' <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> de cet énumérateur.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)