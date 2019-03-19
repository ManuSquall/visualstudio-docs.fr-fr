---
title: Interface IDebugDocumentTextEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentTextEvents interface
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4329af4e440eb9ee0de57a64e6ab55b48b6375b4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150411"
---
# <a name="idebugdocumenttextevents-interface"></a>IDebugDocumentTextEvents, interface
Fournit des événements indiquant les modifications qui ont été apportées au document de texte associé.  
  
> [!NOTE]
>  Le texte du document change lorsque les événements sur cette interface incendie. Gestionnaires d’événements peuvent récupérer le texte à l’aide du `IDebugDocumentText` interface.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugDocumentTextEvents` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|Indique que le document sous-jacent a été détruit et n’est plus valid|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|Indique que le nouveau texte a été ajouté au document|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|Indique que le texte a été supprimé à partir du document.|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|Indique que le texte a été remplacé.|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|Indique que les attributs de texte associés à la plage de position de caractère sous-jacente ont changé.|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|Indique que les attributs de document modifié.|