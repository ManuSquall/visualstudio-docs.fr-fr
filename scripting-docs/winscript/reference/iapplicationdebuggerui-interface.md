---
title: Interface IApplicationDebuggerUI | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IApplicationDebuggerUI interface
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e3c5f9e4cabeb4fba31bb039a7cf673ca1759860
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348904"
---
# <a name="iapplicationdebuggerui-interface"></a>IApplicationDebuggerUI, interface
Implémenté par l’environnement de développement intégré (IDE) de débogueur (en plus de `IApplicationDebugger`) afin de donner un composant externe davantage de contrôle sur l’interface utilisateur (IU) du débogueur.  
  
 Outre les méthodes héritées de `IUnknown`, le `IApplicationDebuggerUI` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|Apporte la fenêtre contenant le document de débogage spécifié vers le haut dans le débogueur de l’interface utilisateur.|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|Met la fenêtre qui contient le contexte de document donné vers le haut de l’interface utilisateur du débogueur et fait défiler la fenêtre pour le contexte.|