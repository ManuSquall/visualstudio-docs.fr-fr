---
title: Les Modes de fonctionnement | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 205837bc5bfdf9476839ea1e54a53dc57dbf9a72
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="operational-modes"></a>Modes de fonctionnement
Il existe trois modes dans lesquels l’IDE peut fonctionner, comme suit :  
  
-   [En Mode Création](#vsconoperationalmodesanchor1)  
  
-   [Mode d’exécution](#vsconoperationalmodesanchor2)  
  
-   [En Mode arrêt](#vsconoperationalmodesanchor3)  
  
 Comment votre moteur de débogage personnalisé (DE) effectue la transition entre ces modes est une décision de mise en œuvre, vous devez être familiarisé avec les mécanismes de transition. Le DE peut ou ne peut pas implémenter directement ces modes. Ces modes sont vraiment package modes débogage qui changent en fonction de l’action de l’utilisateur ou des événements à partir de la DE. Par exemple, le passage du mode d’exécution en mode arrêt est déclenchée par un événement d’arrêt à partir de la DE. La transition à partir de l’arrêt de l’exécuter en mode ou mode pas à pas est déclenchée par l’utilisateur qui effectue des opérations telles que l’étape ou Execute. Pour plus d’informations sur les transitions DE, consultez [contrôle de l’exécution de](../../extensibility/debugger/control-of-execution.md).  
  
##  <a name="vsconoperationalmodesanchor1"></a>En Mode Création  
 Le mode Design est l’état nonrunning de débogage de Visual Studio, au cours de laquelle vous pouvez définir des fonctionnalités dans votre application de débogage.  
  
 Uniquement le débogage quelques fonctionnalités sont utilisées en mode design. Un développeur peut choisir de définir des points d’arrêt ou de créer des expressions espion. Le DE n’est jamais chargé ou appelé alors que l’IDE est en mode design. Interaction avec le DE a lieu pendant les modes d’exécution et d’arrêt uniquement.  
  
##  <a name="vsconoperationalmodesanchor2"></a>Mode d’exécution  
 Mode d’exécution se produit lorsqu’un programme s’exécute dans une session de débogage dans l’IDE. L’application s’exécute jusqu'à l’arrêt, jusqu'à ce qu’un point d’arrêt est atteint ou jusqu'à ce qu’une exception est levée. Lorsque l’application s’exécute à l’arrêt, les transitions DE en mode design. Lorsqu’un point d’arrêt ou une exception est levée, le DE passe en mode arrêt.  
  
##  <a name="vsconoperationalmodesanchor3"></a>En Mode arrêt  
 En mode arrêt se produit lorsque l’exécution du programme de débogage est suspendue. En mode arrêt offre au développeur un instantané de l’application au moment de l’arrêt et permet au développeur d’analyser l’état de l’application et de modifier la façon dont l’application s’exécutera. Le développeur peut afficher et modifier le code, examiner ou modifier des données, redémarrez l’application, fin de l’exécution ou poursuivre l’exécution à partir du même point.  
  
 En mode arrêt est entré lors de la D’envoie un événement d’arrêt synchrones. Les événements d’arrêt synchrones, appelés également les événements d’arrêt, d’informer le Gestionnaire de session de débogage (SDM) et l’IDE de l’application en cours de débogage a arrêté l’exécution de code. Le [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) et [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) les interfaces sont des exemples d’événements d’arrêt.  
  
 Événements d’arrêt sont maintenues par un appel à une des méthodes suivantes, selon lequel effectuer la transition du débogueur à partir du mode d’arrêt pour l’exécution ou en mode pas à pas :  
  
-   [Exécuter](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Continue](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a>Mode pas à pas  
 Mode d’étape se produit lorsque le programme les étapes à la ligne suivante de code, ou détaillé, principal ou en dehors d’une fonction. Une étape est exécutée en appelant la méthode [étape](../../extensibility/debugger/reference/idebugprocess3-step.md). Cette méthode requiert `DWORD`s qui spécifient le [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) et [STEPKIND](../../extensibility/debugger/reference/stepkind.md) énumérations en tant que paramètres d’entrée.  
  
 Lorsque le programme les étapes correctement à la ligne suivante de code ou dans une fonction, ou elle s’exécute jusqu’au curseur ou à un point d’arrêt défini, le DE transitions automatiquement précédent pour le mode arrêt.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle de l’exécution](../../extensibility/debugger/control-of-execution.md)