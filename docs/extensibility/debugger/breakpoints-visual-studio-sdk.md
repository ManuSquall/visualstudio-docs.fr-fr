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
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: fd0eccfa45f20217291b2e00eb175f8eac49d42d
ms.lasthandoff: 02/22/2017

---
# <a name="breakpoints-visual-studio-sdk"></a>Points d’arrêt (Kit de développement logiciel Visual Studio)
Il existe trois types de points d’arrêt : en attente, la liaison et d’erreur.  
  
 **Une attente de point d’arrêt :**  
  
-   Est une abstraction qui contient toutes les informations nécessaires pour lier un point d’arrêt à un ou plusieurs contextes de code dans un ou plusieurs programmes. Chaque fois qu’un programme débogué code motif pour charger, le moteur de débogage qui vérifie des tous les points d’arrêt en attente pour voir si elles peuvent être liées.  
  
     Un point d’arrêt en attente lui-même jamais lie au code, mais plutôt collecte et est dit qu’il contient tous les points d’arrêt le liés qu’il génère.  
  
-   Est représenté par une [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interface.  
  
 **Un point d’arrêt lié :**  
  
-   Est une abstraction pour un point d’arrêt associée ou liée à un contexte de code unique. Chaque point d’arrêt lié est générée en réponse à un point d’arrêt en attente. Un point d’arrêt en attente peut, cependant, génère plusieurs points d’arrêt liés.  
  
     Lorsque le code est déchargé, un point d’arrêt lié peut être indépendant et ignorée.  
  
-   Est représenté par une [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interface.  
  
 **Un point d’arrêt de l’erreur :**  
  
-   Est une abstraction pour la description d’une erreur en tentant de lier un point d’arrêt en attente à un contexte de code. Un point d’arrêt de l’erreur décrit l’erreur emplacement ou dans l’expression du point d’arrêt. Pour plus d’informations, consultez [de liaison des points d’arrêt](../../extensibility/debugger/binding-breakpoints.md).  
  
     L’erreur de point d’arrêt peut être une erreur ou un avertissement.  
  
-   Est représenté par une [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmes](../../extensibility/debugger/programs.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [Contexte de code](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
