---
title: "IDebugProcess2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::Attach"
helpviewer_keywords: 
  - "IDebugProcess2::Attach"
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

joint le gestionnaire de débogage de session \(SDM\) au processus.  
  
## Syntaxe  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```c#  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### Paramètres  
 `pCallback`  
 \[in\]  un objet d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) qui est utilisé pour la notification d'événements de débogage.  
  
 `rgguidSpecificEngines`  
 \[in\]  Un tableau de GUID des moteurs de débogage à utiliser aux programmes de débogage en cours de exécution dans le processus.  ce paramètre peut être une valeur NULL.  Voir notes pour plus de détails.  
  
 `celtSpecificEngines`  
 \[in\]  Le nombre de moteurs de débogage dans le tableau d' `rgguidSpecificEngines` et la taille du tableau d' `rghrEngineAttach` .  
  
 `rghrEngineAttach`  
 \[in, out\]  Un tableau de codes HRESULT retourné par les moteurs de débogage.  La taille de ce tableau est spécifiée dans le paramètre d' `celtSpecificEngines` .  Chaque code est généralement `S_OK` ou `S_ATTACH_DEFERRED`.  Ce dernier indique que le du est actuellement attaché à aucun programmes.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Le tableau suivant montre les autres valeurs possibles.  
  
|Valeur|Description|  
|------------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Le processus spécifié est déjà attachée au débogueur.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Une violation de sécurité s'est produite pendant la procédure d'attachement.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Un processus de bureau ne peut pas être attaché au débogueur.|  
  
## Notes  
 Attacher à un processus attaché le SDM à tous les programmes s'exécutant dans ce processus qui peut être débogué par les moteurs de \(DE\) débogage spécifiés dans le tableau d' `rgguidSpecificEngines` .  Définissez le paramètre d' `rgguidSpecificEngines` à une valeur NULL ou incluez `GUID_NULL` du tableau à attacher à tous les programmes dans le processus.  
  
 tous les événements de débogage qui se produisent dans le processus sont envoyés à l'objet donné d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) .  Cet objet d' `IDebugEventCallback2` est fourni lorsque le SDM appelle cette méthode.  
  
## Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)