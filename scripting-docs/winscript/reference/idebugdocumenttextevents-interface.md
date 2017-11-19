---
title: IDebugDocumentTextEvents (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugDocumentTextEvents interface
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 078cd468b64d30c20f48a3392aa4509ed054fc3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextevents-interface"></a>IDebugDocumentTextEvents, interface
Fournit des événements indiquant des modifications dans le document de texte associée.  
  
> [!NOTE]
>  Le texte du document change lorsque les événements sur cette interface sont activés. Gestionnaires d’événements peuvent récupérer le texte à l’aide du `IDebugDocumentText` interface.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugDocumentTextEvents` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|Indique que le document sous-jacent a été détruit et qu’il n’est plus valide|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|Indique que le nouveau texte a été ajouté au document|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|Indique que le texte a été supprimé du document.|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|Indique que le texte a été remplacé.|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|Indique que les attributs de texte associés à la plage de position de caractère sous-jacente ont changé.|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|Indique que les attributs du document modifié.|