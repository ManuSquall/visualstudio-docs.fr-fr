---
title: "IDiaAddressMap::put_relativeVirtualAddressEnabled | Microsoft Docs"
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
  - "IDiaAddressMap::put_relativeVirtualAddressEnabled (méthode)"
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaAddressMap::put_relativeVirtualAddressEnabled
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

permet au client pour activer ou désactiver le calcul et l'utilisation des adresses virtuelles relatives \(RVA\).  
  
## Syntaxe  
  
```cpp#  
HRESULT put_relativeVirtualAddressEnabled (   
   BOOL NewVal  
);  
```  
  
#### Paramètres  
 NewVal  
 \[in\]  Affectez à `TRUE` pour activer, ou à `FALSE` à effacer.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Les adresses pour les objets de débogage décrits par les interfaces de diamètre, et par rapport à la base de l'image du fichier exécutable, peuvent être récupérées comme adresses virtuelles relatives.  
  
 L'utilisation de Virtuelles est activée lorsque les segments sont initialement chargés à partir d'un fichier PDB.  Pour obtenir l'état actuel de l'utilisation de Virtuelles, appelez la méthode d' [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) .  
  
 La méthode d' `put_relativeVirtualAddress` doit être appelée pour activer Virtuelles après un appel réussi à la méthode d' [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) a établi de nouveaux en\-têtes d'image.  
  
## Voir aussi  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)