---
title: "IDebugDocumentTextEvents, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentTextEvents (interface)"
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextEvents, interface
Fournit des événements qui indique les modifications apportées au document texte associé.  
  
> [!NOTE]
>  Le texte du document change lorsque les événements sur cette interface les déclenchent.  Les gestionnaires d'événements peuvent récupérer le nouveau texte à l'aide de l'interface d' `IDebugDocumentText` .  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IDebugDocumentTextEvents` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|Indique que le document sous\-jacent a perdu et n'est plus valide|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|Indique que le nouveau texte a été ajouté au document|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|Indique que le texte a été supprimé du document.|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|Indique que le texte a été remplacé.|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|Indique que les attributs du texte associés à la plage sous\-jacent de la position du caractère ont changé.|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|Indique que les attributs de document ont changé.|