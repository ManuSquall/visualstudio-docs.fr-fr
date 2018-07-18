---
title: IEnumDebugCodeContexts2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc6ff9a173bcfbb87606fe493697857d7ec2b323
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122559"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Cette interface énumère les contextes de code associé liés la session de débogage, ou à un document ou un programme particulier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface pour représenter une liste de contextes de code pour une position de texte spécifique dans un programme, ou une liste de contextes de code pour un contexte de document particulier.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Appelez [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) pour obtenir cette interface qui représente une liste de contextes de code pour une position d’un texte spécifique dans le document d’origine d’un programme.  
  
 Appelez [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) pour obtenir cette interface qui représente une liste de tous les contextes de code dans un document source particulier.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumDebugCodeContexts2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Récupère un nombre spécifié de contextes de code dans une séquence d’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Ignore un nombre spécifié de contextes de code dans une séquence d’énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Réinitialise la séquence d’énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Obtient le nombre de contextes de code dans un énumérateur.|  
  
## <a name="remarks"></a>Notes  
 Appels de Visual Studio [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) pour remplir une liste de contextes de code de l’utilisateur peut choisir à partir de laquelle définir l’instruction suivante ou en affichant le code machine pour un fichier source. Plusieurs contextes de code peuvent se produire, par exemple, lorsqu’il y a plusieurs instances d’un modèle de style C++.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)