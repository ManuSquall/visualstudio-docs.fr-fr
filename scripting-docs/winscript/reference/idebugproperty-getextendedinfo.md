---
title: "IDebugProperty::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.GetExtendedInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::GetExtendedInfo"
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::GetExtendedInfo
Obtient les informations étendues pour la propriété.  
  
## Syntaxe  
  
```  
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### Paramètres  
 `cInfos`  
 \[in\]  nombre d'objets des informations étendues.  
  
 `rgguidExtendedInfo`  
 \[in\]  Un tableau d' `GUID`s est passée afin que plusieurs éléments des informations étendues peuvent être récupérés en même temps.  
  
 `pExtendedInfo`  
 \[out\]  Retourne un tableau d' `VARIANT`s qui peut être utilisée pour récupérer des informations de propriété étendue.  
  
## Valeur de retour  
 Retourne `HRESULT`valide, en général `S_OK`.  
  
## Notes  
 Cette interface obtient les informations étendues pour cet objet.  L'API existe uniquement pour les besoins de récupérer les informations qui ne se prêtent pas à être récupéré par l'utilisation `IDebugProperty::GetPropertyInfo`\).  
  
## Voir aussi  
 [IDebugProperty, interface](../../winscript/reference/idebugproperty-interface.md)