---
title: "IPerPropertyBrowsing2, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2 (interface)"
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IPerPropertyBrowsing2, interface
Accède aux informations dans les pages de propriétés offertes par un objet.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|`GetDisplayString`|Retourne une chaîne de texte décrivant la propriété spécifiée.|  
|`MapPropertyToPage`|Retourne le CLSID de la page de propriétés qui permet la manipulation de la propriété spécifiée.|  
|`GetPredefinedStrings`|Retourne un tableau de chaînes compté \(pointeurs d'`LPOLESTR` \) répertoriant les descriptions des valeurs autorisées que la propriété spécifiée peut recevoir.|  
|`SetPredefinedValue`|Définit la valeur de la propriété la valeur prédéfinie identifiée par `dwCookie.`de jeton|  
  
## Configuration requise  
 En\-tête : dbgprop.h