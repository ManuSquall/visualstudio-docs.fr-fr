---
title: "IEnumDebugCodeContexts2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugCodeContexts2"
helpviewer_keywords: 
  - "IEnumDebugCodeContexts2"
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IEnumDebugCodeContexts2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface énumère les contextes de code associés à la session de débogage, ou avec un programme ou un document spécifique.  
  
## Syntaxe  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur \(DE\) de débogage implémente cette interface pour représenter une liste des contextes de code pour un emplacement de texte particulier dans un programme, ou une liste des contextes de code pour un contexte de document spécifique.  
  
## Remarques pour les appelants  
 Appelez [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) pour obtenir cette interface représentant une liste des contextes de code pour un emplacement de texte spécifique dans le document source d'un programme.  
  
 appelez [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) pour obtenir cette interface représentant une liste de tous les contextes de code dans un document source particulier.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IEnumDebugCodeContexts2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Suivant](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Récupère un nombre spécifié de contextes de code dans une séquence d'énumération.|  
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Ignore un nombre spécifié de contextes de code dans une séquence d'énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|réinitialise une séquence d'énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|obtient le nombre de contextes de code dans un énumérateur.|  
  
## Notes  
 Visual Studio appelle [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) pour remplir la liste des contextes de code que l'utilisateur peut choisir de en définissant l'instruction suivante ou en affichant le code machine d'un fichier source.  Plusieurs contextes de code peuvent se produire, par exemple, lorsqu'il existe plusieurs instances de modèle C\/C\+\+ \+\+\-style.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)