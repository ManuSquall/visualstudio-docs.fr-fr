---
title: Interface IProvideExpressionContexts | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: b6ec0d5e17b0d3527252352c2e789adfac4fa859
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63410042"
---
# <a name="iprovideexpressioncontexts-interface"></a>IProvideExpressionContexts, interface
Fournit un moyen d’énumérer les contextes d’expression connus d’un certain composant. En général, les moteurs de script implémentent cette interface.  
  
 Le Gestionnaire de débogage de processus utilise cette interface pour trouver tous les contextes d’expression globale associées à un thread donné.  
  
> [!NOTE]
> Cette interface est appelée à partir du thread d’intérêt. Il est à l’implémenteur pour identifier le thread actuel et retourne un énumérateur approprié.  
  
## <a name="methods"></a>Méthodes  
 Outre les méthodes héritées de `IUnknown`, le `IProvideExpressionContexts` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Retourne un énumérateur des contextes d’expression connus par ce composant.|