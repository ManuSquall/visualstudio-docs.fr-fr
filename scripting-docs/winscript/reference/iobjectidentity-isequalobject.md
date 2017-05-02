---
title: "IObjectIdentity::IsEqualObject | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IObjectIdentity.IsEqualObject
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IsEqualObject (méthode)"
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IObjectIdentity::IsEqualObject
Détermine si un objet est égal à l'objet actuel.  
  
## Syntaxe  
  
```  
HRESULT IsEqualObject(  
  IUnknown*  punk  
);  
```  
  
#### Paramètres  
 `punk`  
 \[in\]  Adresse de l'objet à comparer avec l'objet actuel.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|Les objets sont égaux.|  
|`S_FALSE`|Les objets ne sont pas égales.|  
  
## Notes  
 Une implémentation de la méthode d' `IsEqualObject` doit retourner `S_OK` uniquement si les objets sont identiques.  
  
## Voir aussi  
 [IObjectIdentity, interface](../../winscript/reference/iobjectidentity-interface.md)