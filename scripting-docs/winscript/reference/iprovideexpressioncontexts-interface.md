---
title: Interface IProvideExpressionContexts | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProvideExpressionContexts interface
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91f4251fec57001ba6c7a4ea1804ec72371418bb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345095"
---
# <a name="iprovideexpressioncontexts-interface"></a>IProvideExpressionContexts, interface
Fournit un moyen d’énumérer les contextes d’expression connus d’un certain composant. En général, les moteurs de script implémentent cette interface.  
  
 Le Gestionnaire de débogage de processus utilise cette interface pour trouver tous les contextes d’expression globale associées à un thread donné.  
  
> [!NOTE]
>  Cette interface est appelée à partir du thread d’intérêt. Il est à l’implémenteur pour identifier le thread actuel et retourne un énumérateur approprié.  
  
## <a name="methods"></a>Méthodes  
 Outre les méthodes héritées de `IUnknown`, le `IProvideExpressionContexts` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Retourne un énumérateur des contextes d’expression connus par ce composant.|