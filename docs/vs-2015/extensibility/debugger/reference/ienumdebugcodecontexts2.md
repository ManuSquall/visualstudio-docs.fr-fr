---
title: IEnumDebugCodeContexts2 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 387dce09ee6a01b2ff092e963fa4197d833ef142
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507795"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IEnumDebugCodeContexts2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugcodecontexts2).  
  
Cette interface énumère les contextes de code associé liés la session de débogage, ou à un document ou un programme particulier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Le moteur de débogage (dé) implémente cette interface pour représenter une liste des contextes de code à un emplacement de texte particulier dans un programme ou une liste des contextes de code pour un contexte de document particulier.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Appelez [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) pour obtenir cette interface représentant la liste des contextes de code à un emplacement de texte spécifique dans le document de source d’un programme.  
  
 Appelez [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) pour obtenir cette interface représentant une liste de tous les contextes de code dans un document de code source particulier.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumDebugCodeContexts2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Récupère un nombre spécifié de contextes de code dans une séquence d’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Ignore un nombre spécifié de contextes de code dans une séquence d’énumération.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Réinitialise une séquence d’énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur en cours.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Obtient le nombre de contextes de code dans un énumérateur.|  
  
## <a name="remarks"></a>Notes  
 Les appels de Visual Studio [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) pour remplir une liste des contextes de code, l’utilisateur peut choisir à partir de laquelle définir l’instruction suivante ou en affichant le code machine pour un fichier source. Plusieurs contextes de code peuvent se produire, par exemple, lorsqu’il existe plusieurs instances d’un modèle de style C++.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)

