---
title: IApplicationDebuggerUI (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IApplicationDebuggerUI interface
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbaa04f6790ffc4d80447a6745ca82cc8dba6802
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggerui-interface"></a>IApplicationDebuggerUI, interface
Implémenté par l’environnement de développement intégré (IDE) de débogueur (en plus de `IApplicationDebugger`) pour permettre à un composant externe davantage de contrôle sur l’interface utilisateur (IU) du débogueur.  
  
 Outre les méthodes héritées de `IUnknown`, le `IApplicationDebuggerUI` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|Met la fenêtre contenant le document de débogage spécifiés vers le haut dans le débogueur de l’interface utilisateur.|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|Affiche la fenêtre contenant le contexte de document donné vers le haut de l’interface utilisateur du débogueur et fait défiler la fenêtre vers le contexte.|