---
title: Points d’arrêt (Kit de développement logiciel Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39c13271bad984291f609ef45505549855bee99f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68146418"
---
# <a name="breakpoints-visual-studio-sdk"></a>Points d’arrêt (SDK Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il existe trois types de points d’arrêt : en attente, la limite et d’erreur.  
  
 **Un en attente de point d’arrêt :**  
  
- Est une abstraction qui contient toutes les informations nécessaires pour lier un point d’arrêt à un ou plusieurs contextes de code dans un ou plusieurs programmes. Chaque fois qu’un programme débogué code cause à charger, le moteur de débogage qui consulte des tous les points d’arrêt en attente pour voir si elles peuvent être liées.  
  
   Un point d’arrêt en attente lui-même jamais lie au code, mais plutôt collecte et est dit qu’il contient tous les points d’arrêt les liés qu’il génère.  
  
- Est représenté par un [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interface.  
  
  **Un point d’arrêt lié :**  
  
- Est une abstraction pour un point d’arrêt associée ou liée à un contexte de code unique. Chaque point d’arrêt lié est généré en réponse à un point d’arrêt en attente. Un point d’arrêt en attente peut, toutefois, générer plus d’un point d’arrêt lié.  
  
   Lorsque le code est déchargé, un point d’arrêt lié peut être indépendant et ignorée.  
  
- Est représenté par un [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interface.  
  
  **Un point d’arrêt de l’erreur :**  
  
- Est une abstraction pour la description d’une erreur dans la tentative de liaison d’un point d’arrêt en attente à un contexte de code. Un point d’arrêt de l’erreur décrit une erreur dans l’emplacement ou dans l’expression de point d’arrêt lui-même. Pour plus d’informations, consultez [liaison des points d’arrêt](../../extensibility/debugger/binding-breakpoints.md).  
  
   L’erreur de point d’arrêt peut être une erreur ou un avertissement.  
  
- Est représenté par un [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmes](../../extensibility/debugger/programs.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [Contexte de code](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
