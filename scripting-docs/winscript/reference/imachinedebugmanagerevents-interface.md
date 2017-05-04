---
title: "IMachineDebugManagerEvents, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IMachineDebugManagerEvents (interface)"
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManagerEvents, interface
Les modifications de signaux de la liste d'application active mise à jour par l'ordinateur de débogage le gestionnaire.  Cette interface peut être utilisée par le débogueur IDE pour afficher une liste dynamique d'applications.  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IMachineDebugManagerEvents` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Gère l'événement lorsqu'une application est ajoutée à la liste d'application active.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Gère l'événement lorsqu'une application est supprimée de la liste d'application active.|