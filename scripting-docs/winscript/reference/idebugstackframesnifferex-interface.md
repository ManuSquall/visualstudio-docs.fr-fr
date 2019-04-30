---
title: Interface IDebugStackFrameSnifferEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSnifferEx interface
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dccd9210908922951c20378868c33b3389cbed4f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432249"
---
# <a name="idebugstackframesnifferex-interface"></a>IDebugStackFrameSnifferEx, interface
Fournit un moyen pour énumérer les frames de pile logique appelées par un composant. En général, les moteurs de script implémentent cette interface. Le processus débogage Gestionnaire utilise cette interface pour trouver tous les frames de pile associée à un thread donné.  
  
> [!NOTE]
> Cette interface est appelée à partir du thread d’intérêt. L’implémentation d’interface doit identifier le thread actuel et retourne un énumérateur approprié.  
  
 Outre les méthodes héritées de `IDebugStackFrameSniffer`, le `IDebugStackFrameSnifferEx` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Retourne un énumérateur de frames de pile pour le thread actuel.|