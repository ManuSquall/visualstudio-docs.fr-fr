---
title: IDebugDocumentTextEvents2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b574ae45dafed11ed28047859676524054951512
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65678972"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface permet de notifier à Visual Studio les modifications apportées au document source qui sont fournies par le moteur de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le DE implémente cette interface pour prendre en charge l’apport de modifications au code source. Cette interface est généralement implémentée sur le même objet qui implémente l’interface [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .  
  
## <a name="notes-for-callers"></a>Notes pour les appelants  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Obtient cette interface via un appel à la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> méthode. L' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface est obtenue à partir d’un appel à la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> méthode. L' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface est obtenue en appelant la méthode [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) sur une interface [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugDocumentTextEvents2` .  
  
|Méthode|Description|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Indique que l’intégralité du document a été détruite.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Notifie le package de débogage que du texte a été inséré dans le document.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Notifie le package de débogage que du texte a été supprimé du document.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Notifie le package de débogage que du texte a été remplacé dans le document.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Informe le package de débogage que des attributs de texte ont été mis à jour dans le document.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Avertit le destinataire de l’événement que les attributs du document ont été mis à jour.|  
  
## <a name="remarks"></a>Notes  
 Seuls les moteurs de débogage qui fournissent leurs propres documents tirent parti de l' `IDebugDocumentTextEvent2` interface. Par exemple, un moteur de débogage de script. Dans le processus d’interprétation des scripts, il est possible de générer un nouveau code source qui n’est présent dans aucun fichier disque et qui est connu uniquement du DE.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
