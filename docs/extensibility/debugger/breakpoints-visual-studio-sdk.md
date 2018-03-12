---
title: "Points d’arrêt (Kit de développement logiciel Visual Studio) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: be8f0b36ebe57041e9d36b8f606bd5bddd0601bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="breakpoints-visual-studio-sdk"></a>Points d’arrêt (Kit de développement logiciel Visual Studio)
Il existe trois types de points d’arrêt : en attente, la limite et d’erreur.  
  
 **Un en attente de point d’arrêt :**  
  
-   Est une abstraction qui contient toutes les informations nécessaires pour lier un point d’arrêt à un ou plusieurs contextes de code dans un ou plusieurs programmes. Chaque fois qu’un programme débogué code cause à charger, le moteur de débogage qui consulte des tous les points d’arrêt en attente pour voir si elles peuvent être liés.  
  
     Un point d’arrêt en attente lui-même jamais lie au code, mais plutôt collecte et est dit pour contenir tous les points d’arrêt les liés qu’elle génère.  
  
-   Est représenté par un [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interface.  
  
 **Un point d’arrêt lié :**  
  
-   Est une abstraction pour un point d’arrêt associée ou liée à un contexte de code unique. Chaque point d’arrêt lié est générée en réponse à un point d’arrêt en attente. Un point d’arrêt en attente peut, cependant, générer plus d’un point d’arrêt lié.  
  
     Lorsque le code est déchargé, un point d’arrêt lié peut être indépendant et ignorée.  
  
-   Est représenté par un [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interface.  
  
 **Un point d’arrêt de l’erreur :**  
  
-   Est une abstraction pour la description d’une erreur lors de la tentative lier un point d’arrêt en attente à un contexte de code. Un point d’arrêt de l’erreur décrit l’erreur emplacement ou dans l’expression de point d’arrêt elle-même. Pour plus d’informations, consultez [de liaison des points d’arrêt](../../extensibility/debugger/binding-breakpoints.md).  
  
     L’erreur de point d’arrêt peut être une erreur ou un avertissement.  
  
-   Est représenté par un [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmes](../../extensibility/debugger/programs.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [Contexte de code](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)