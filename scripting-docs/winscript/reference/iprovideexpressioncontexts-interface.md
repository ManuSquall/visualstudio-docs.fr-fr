---
title: IProvideExpressionContexts (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IProvideExpressionContexts interface
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 402b439da6f1fa369accacb27f987ac77119e343
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iprovideexpressioncontexts-interface"></a>IProvideExpressionContexts, interface
Fournit un moyen pour énumérer les contextes d’expression connus par un certain composant. En général, les moteurs de script implémentent cette interface.  
  
 Le Gestionnaire de processus de débogage utilise cette interface pour rechercher tous les contextes d’expression globale associées à un thread donné.  
  
> [!NOTE]
>  Cette interface est appelée à partir du thread d’intérêt. C’est à l’implémenteur d’identifier le thread actuel et retourne un énumérateur approprié.  
  
## <a name="methods"></a>Méthodes  
 Outre les méthodes héritées de `IUnknown`, le `IProvideExpressionContexts` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Retourne un énumérateur de contextes d’expression connu par ce composant.|