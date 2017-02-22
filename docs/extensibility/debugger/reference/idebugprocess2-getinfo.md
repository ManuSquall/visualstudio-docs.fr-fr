---
title: "IDebugProcess2::GetInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::GetInfo"
helpviewer_keywords: 
  - "IDebugProcess2::GetInfo"
ms.assetid: 46021dce-bb97-46c3-b0cc-e5b3b68acc35
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProcess2::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient une description du processus.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetInfo(  
   PROCESS_INFO_FIELDS  Fields,  
   PROCESS_INFO*        pProcessInfo  
);  
```  
  
```c#  
int GetInfo(  
   enum_PROCESS_INFO_FIELDS  Fields,  
   PROCESS_INFO[]            pProcessInfo  
);  
```  
  
#### Paramètres  
 `Fields`  
 \[in\]  Une combinaison des valeurs de l'énumération de [PROCESS\_INFO\_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) qui spécifie les champs du paramètre d' `pProcessInfo` doivent être effectués.  
  
 `pProcessInfo`  
 \[out\]  Une structure de [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) qui est terminée avec une description du processus.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [PROCESS\_INFO\_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)