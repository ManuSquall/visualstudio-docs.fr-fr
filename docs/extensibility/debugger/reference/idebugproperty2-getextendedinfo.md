---
title: "IDebugProperty2::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetExtendedInfo"
helpviewer_keywords: 
  - "IDebugProperty2::GetExtendedInfo"
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty2::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient les informations détaillées pour la propriété.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```c#  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### Paramètres  
 `guidExtendedInfo`  
 \[in\]  GUID qui détermine le type d'informations détaillées à récupérer.  Voir notes pour plus de détails.  
  
 `pExtendedInfo`  
 \[out\]  Retourne `VARIANT` \(C\+\+\) ou un objet \(c\#\) qui peuvent être utilisés pour récupérer des informations de propriété étendue.  Par exemple, ce paramètre peut retourner une interface d' `IUnknown` qui peut être interrogé pour une interface d' [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) .  Voir notes pour plus de détails.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne un code d'erreur.  Retourne `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` s'il n'y a aucune information étendues à récupérer.  
  
## Notes  
 Cette méthode existe dans le but d'extraire des informations qui ne se prêtent pas à être récupéré en appelant la méthode d' [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) .  
  
 Les GUID suivant sont généralement identifiés par cette méthode \(les valeurs du GUID sont spécifiées pour c\# comme le nom est pas disponible dans n'importe quel assembly\).  GUID supplémentaire peut être créé pour un usage interne.  
  
|Nom|GUID|Description|  
|---------|----------|-----------------|  
|guidDocument|{} 3f98de84\-fee9\-11d0\-b47f\-00a0244a1dd2|Retourne une interface d' `IUnknown` au document.  En général, l'interface d' [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) peut être obtenu à partir de cette interface d' `IUnknown` .|  
|guidCodeContext|{} e2fc65e\-56ce\-11d1\-b528\-00aax004a8797|Retourne une interface d' `IUnknown` au contexte de document.  En général, l'interface d' [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) peut être obtenu à partir de cette interface d' `IUnknown` .|  
|guidCustomViewerSupported|{} d9c9da31\-ffbe\-4eeb\-9186\-23121e3c088c|Retourne une chaîne contenant le CLSID d'une visionneuse personnalisée, généralement implémenté par un évaluateur d'expression.|  
|guidExtendedInfoSlot|{} 6df235ad\-82c6\-4292\-9c97\-7389770bc42f|Retourne un nombre 32 bits représentant le numéro d'emplacement souhaité si cette propriété représente une adresse locale de code managé.|  
|guidExtendedInfoSignature|{} b5fb6d46\-f805\-417f\-96a3\-8ba737073ffd|Retourne une chaîne contenant la signature de la variable associée à l'objet de propriété.|  
  
## Voir aussi  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)