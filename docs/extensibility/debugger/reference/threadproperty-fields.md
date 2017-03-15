---
title: "THREADPROPERTY_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "THREADPROPERTY_FIELDS"
helpviewer_keywords: 
  - "Énumération de THREADPROPERTY_FIELDS"
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie les informations sur un thread doivent être récupérées.  
  
## Syntaxe  
  
```cpp#  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```c#  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## Membres  
 TPF\_ID  
 Initialisez\/utilisez le champ d' `dwThreadId` de la structure de [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) .  
  
 TPF\_SUSPENDCOUNT  
 Initialisez\/utilisez le champ d' `dwSuspendCount` de la structure d' `THREADPROPERTIE`S.  
  
 TPF\_STATE  
 Initialisez\/utilisez le champ d' `dwThreadState` de la structure d' `THREADPROPERTIE`S.  
  
 TPF\_PRIORITY  
 Initialisez\/utilisez le champ d' `bstrPriority` de la structure d' `THREADPROPERTIE`S.  
  
 TPF\_NAME  
 Initialisez\/utilisez le champ d' `bstrName` de la structure d' `THREADPROPERTIE`S.  
  
 TPF\_LOCATION  
 Initialisez\/utilisez le champ d' `bstrLocation` de la structure d' `THREADPROPERTIE`S.  
  
 TPF\_ALLFIELDS  
 spécifie tous les champs.  
  
## Notes  
 Ces valeurs sont passées comme un argument à la méthode d' [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) pour indiquer que des champs de la structure de [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) doivent être initialisé.  
  
 Ces valeurs sont également utilisées dans le membre d' `dwFields` de la structure d' `THREADPROPERTIES` pour indiquer les champs sont utilisés et valides.  
  
 Ces indicateurs peuvent être combinées avec `OR`de bits.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)