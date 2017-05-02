---
title: "IActiveScriptProfilerControl::StartProfiling | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerControl.StartProfiling
apilocation: scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerControl::StartProfiling
Démarre le profilage sur le moteur de script.  Le moteur de script crée une instance de l'objet de profileur en appelant à [CoCreateInstance](http://msdn.microsoft.com/fr-fr/7295a55b-12c7-4ed0-a7a4-9ecee16afdec).  
  
## Syntaxe  
  
```  
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### Paramètres  
 `clsidProfilerObject`  
 \[in\]  Identificateur de classe \(CLSID\) de l'objet de profileur à créer.  
  
 `dwEventMask`  
 \[in\]  Un masque de bits 4 octets qui spécifie les types d'événements.  Les bits sont définis dans [PROFILER\_EVENT\_MASK, énumération](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
 `dwContext`  
 \[in\]  Une valeur de 4 octets passé à l'objet de profileur.  
  
## Valeur de retour  
 Retourne un HRESULT.  Les valeurs possibles sont les suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|`S_OK`|La méthode a réussi.|  
|`ACTIVPROF_E_PROFILER_PRESENT`|Le profilage est déjà activé.|  
  
## Voir aussi  
 [IActiveScriptProfilerControl, interface](../../winscript/reference/iactivescriptprofilercontrol-interface.md)