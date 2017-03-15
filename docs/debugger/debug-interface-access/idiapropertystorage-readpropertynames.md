---
title: "IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadPropertyNames"
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère les noms de chaîne correspondants pour les identificateurs donnés de propriété.  
  
## Syntaxe  
  
```cpp  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### Paramètres  
 `cpropid`  
 \[in\]  Numéro d'ID de propriété dans `rgpropid`.  
  
 `rgpropid`  
 \[in\]  Tableau d'identificateurs de propriété pour lesquels obtiennent les noms \(`PROPID` est défini dans WTypes.h comme `ULONG`\).  
  
 `rglpwstrName`  
 \[in, out\]  Choix de noms de propriété pour les ID spécifiés de propriété.  Le tableau doit être pré\-allouée pour contenir le nombre demandé de noms de propriété et doit pouvoir accueillir au minimum des chaînes d' `cpropid``BSTR` .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne un code d'erreur.  
  
## Notes  
 Les noms de propriétés retournés doivent être libérés \(en appelant la fonction de `SysFreeString` \) lorsqu'ils ne sont plus nécessaires.  
  
## Voir aussi  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)