---
title: "IDiaAddressMap::set_imageHeaders | Microsoft Docs"
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
  - "IDiaAddressMap::set_imageHeaders (méthode)"
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaAddressMap::set_imageHeaders
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Définit des en\-têtes d'image pour activer la translation d'adresses d'adresse virtuelle associée.  
  
## Syntaxe  
  
```cpp#  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### Paramètres  
 cbData  
 \[in\]  Nombre d'octets de données d'en\-tête.  doit être `n*sizeof(IMAGE_SECTION_HEADER)` où `n` est le nombre d'intitulés dans le fichier exécutable.  
  
 données \[\]  
 \[in\]  Un tableau de structures d' `IMAGE_SECTION_HEADER` à utiliser comme en\-têtes d'image.  
  
 originalHeaders  
 \[in\]  Affectez à `FALSE` si les en\-têtes d'image sont de la nouvelle image, `TRUE` s'ils reflètent l'image d'origine avant une mise à niveau.  En général, cela serait définie à `TRUE` uniquement en combinaison avec des appels à la méthode d' [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 La structure d' `IMAGE_SECTION_HEADER` est déclarée dans Winnt.h et représente le format de l'intitulé d'image du fichier exécutable.  
  
 Les calculs d'adresse virtuelle connexes dépendent des valeurs d' `IMAGE_SECTION_HEADER` .  Généralement, le diamètre extrait ces derniers à partir de le fichier de base de données du programme \(.pdb\).  Si ces valeurs sont absentes, le diamètre ne peut pas calculer les adresses virtuelles relatives et la méthode d' [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) retourne `FALSE`.  Le client doit ensuite appeler la méthode d' [IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) pour activer les calculs d'adresse virtuelle connexes après avoir fourni les en\-têtes manquants de l'image de l'image lui\-même.  
  
## Voir aussi  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)