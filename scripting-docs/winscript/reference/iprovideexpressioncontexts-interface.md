---
title: "IProvideExpressionContexts, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IProvideExpressionContexts (interface)"
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProvideExpressionContexts, interface
Permet d'énumérer des contextes d'expression connus par un certain composant.  Les moteurs de script implémentent généralement cette interface.  
  
 Le processus de débogage utilise de gestionnaire cette interface pour rechercher tous les contextes globaux d'expression associés à un thread donné.  
  
> [!NOTE]
>  Cette interface est appelée du thread concerné.  Elle appartient à l'implémenteur pour identifier le thread actuel et pour retourner un énumérateur approprié.  
  
## Méthodes  
 Outre les méthodes héritées de `IUnknown`, l'interface `IProvideExpressionContexts` expose les méthodes suivantes.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Retourne un énumérateur des contextes d'expression connus par ce composant.|