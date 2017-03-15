---
title: "BPERESI_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BPERESI_FIELDS"
helpviewer_keywords: 
  - "Énumération de BPERESI_FIELDS"
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# BPERESI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie les informations à récupérer à propos d'une résolution d'un point d'arrêt.  
  
## Syntaxe  
  
```cpp#  
enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD BPERESI_FIELDS;  
```  
  
```c#  
public enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
```  
  
## Membres  
 PERESI\_BPRESLOCATION  
 Initialisez\/utilisez le champ d' `bpResLocation` \(emplacement de résolution de point d'arrêt\) de la structure de [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) .  
  
 BPERESI\_PROGRAM  
 Initialisez\/utilisez le champ d' `pProgram` de la structure d' `BP_ERROR_RESOLUTION_INFO` .  
  
 BPERESI\_THREAD  
 Initialisez\/utilisez le champ d' `pThread` de la structure d' `BP_ERROR_RESOLUTION_INFO` .  
  
 BPERESI\_MESSAGE  
 Initialisez\/utilisez le champ d' `bstrMessage` de la structure d' `BP_ERROR_RESOLUTION_INFO` .  
  
 BPERESI\_TYPE  
 Initialisez\/utilisez le champ d' `dwType` \(types de points d'arrêt\) de la structure d' `BP_ERROR_RESOLUTION_INFO` .  
  
 BPERESI\_ALLFIELDS  
 Initialisez\/utiliser tous les champs de la structure d' `BP_ERROR_RESOLUTION_INFO` .  
  
## Notes  
 Passé comme un paramètre à la méthode de [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) indiquer que des champs de la structure de [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) doivent être initialisé.  
  
 Ces valeurs sont également utilisées pour indiquer que les champs de la structure d' `BP_ERROR_RESOLUTION_INFO` sont utilisés et valides lorsque cette structure est retournée.  
  
 Ces valeurs peuvent être combinées avec `OR`de bits.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)