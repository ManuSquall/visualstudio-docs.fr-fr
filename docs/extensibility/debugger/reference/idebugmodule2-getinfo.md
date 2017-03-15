---
title: "IDebugModule2::GetInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule2::GetInfo"
helpviewer_keywords: 
  - "Méthode GetInfo"
  - "IDebugModule2::GetInfo (méthode)"
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugModule2::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient des informations sur ce module.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetInfo(   
   MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO*       pInfo  
);  
```  
  
```cpp#  
int GetInfo(   
   enum_MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO[]           pInfo  
);  
```  
  
#### Paramètres  
 `dwFields`  
 \[in\]  Une combinaison des indicateurs d'énumération de [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) qui spécifient les champs d' `pInfo` doivent être effectués.  
  
 `pInfo`  
 \[in, out\]  Une structure de [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) qui est terminée avec une description du module.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 La structure de [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) contient le nom du module qui s'affiche dans la fenêtre du **Module** .  
  
## Voir aussi  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)