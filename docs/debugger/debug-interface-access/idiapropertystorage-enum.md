---
title: "IDiaPropertyStorage::Enum | Microsoft Docs"
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
  - "IDiaPropertyStorage::Enum"
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaPropertyStorage::Enum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Obtient un énumérateur pour les propriétés de cet ensemble.  
  
## Syntaxe  
  
```cpp#  
HRESULT Enum (   
   IEnumSTATPROPSTG** ppenum  
);  
```  
  
#### Paramètres  
 `ppenum`  
 \[out\]  Retourne un objet d' `IEnumSTATPROPSTG` \(dans l'espace de noms Microsoft.VisualStudio.OLE.Interop\) représentant une énumération de propriétés.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)