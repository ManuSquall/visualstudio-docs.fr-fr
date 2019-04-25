---
title: Les Modes de fonctionnement | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4009ab6268140117c8fd1294adcc52ac347b799
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60087805"
---
# <a name="operational-modes"></a>Modes de fonctionnement
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il existe trois modes dans lesquels l’IDE peut fonctionner, comme suit :  
  
- [Mode Création](#vsconoperationalmodesanchor1)  
  
- [Mode d’exécution](#vsconoperationalmodesanchor2)  
  
- [Mode arrêt](#vsconoperationalmodesanchor3)  
  
  Comment votre moteur de débogage personnalisé (dé) effectue la transition entre ces modes est une décision d’implémentation que vous devez être familiarisé avec les mécanismes de transition. Le DE peut ou ne peut pas implémenter directement ces modes. Ces modes sont vraiment package modes de débogage qui changent en fonction de l’action de l’utilisateur ou des événements à partir de l’Allemagne. Par exemple, la transition du mode d’exécution en mode arrêt est déclenchée par un événement d’arrêt à partir de l’Allemagne. La transition à partir de l’arrêt de l’exécuter en mode ou mode pas à pas est déclenchée par l’utilisateur qui effectue des opérations telles que l’étape ou Execute. Pour plus d’informations sur les transitions DE, consultez [contrôle d’exécution](../../extensibility/debugger/control-of-execution.md).  
  
## <a name="vsconoperationalmodesanchor1"></a> Mode Création  
 Le mode Design est l’état nonrunning de débogage de Visual Studio, au cours de laquelle vous pouvez définir des fonctionnalités dans votre application de débogage.  
  
 Uniquement le débogage quelques fonctionnalités sont utilisées en mode design. Un développeur peut choisir de définir des points d’arrêt ou de créer des expressions espion. Le dé n’est jamais chargé ou appelée alors que l’IDE est en mode design. Interaction avec le dé a lieu au cours des modes d’exécution et d’arrêt uniquement.  
  
## <a name="vsconoperationalmodesanchor2"></a> Mode d’exécution  
 Mode d’exécution se produit lorsqu’un programme s’exécute dans une session de débogage dans l’IDE. L’application s’exécute jusqu'à l’arrêt, jusqu'à ce qu’un point d’arrêt est atteint, ou jusqu'à ce qu’une exception est levée. Lorsque l’application s’exécute à l’arrêt, les transitions DE en mode design. Lorsqu’un point d’arrêt est atteint, ou une exception est levée, le DE passe en mode arrêt.  
  
## <a name="vsconoperationalmodesanchor3"></a> Mode arrêt  
 Mode arrêt se produit lorsque l’exécution du programme de débogage est suspendue. Mode arrêt offre au développeur un instantané de l’application au moment de l’arrêt et permet au développeur d’analyser l’état de l’application et de modifier la façon dont l’application s’exécutera. Le développeur peut afficher et modifier le code, examiner ou modifier des données, redémarrez l’application, fin d’exécution ou poursuivre l’exécution à partir du même point.  
  
 Mode arrêt est entré lors de l’Allemagne envoie un événement d’arrêt synchrones. Événements synchrones en cours d’arrêt, également appelés événements de l’arrêt, notifient le Gestionnaire de session de débogage (SDM) et l’IDE de l’application en cours de débogage a arrêté l’exécution de code. Le [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) et [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) interfaces sont des exemples d’événements d’arrêt.  
  
 Événements d’arrêt sont maintenues par un appel à une des méthodes suivantes, le débogueur à partir du mode arrêt à exécuter ou à l’étape de mode de transition :  
  
- [Execute](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
- [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
- [Continue](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
### <a name="vsconoperationalmodesanchor4"></a> Mode pas à pas  
 Mode de l’étape se produit lorsque le programme les étapes à la ligne suivante de code, ou dans, au-dessus ou en dehors d’une fonction. Une étape est exécutée en appelant la méthode [étape](../../extensibility/debugger/reference/idebugprocess3-step.md). Cette méthode nécessite `DWORD`s qui spécifient le [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) et [STEPKIND](../../extensibility/debugger/reference/stepkind.md) énumérations en tant que paramètres d’entrée.  
  
 Lorsque le programme avec succès les étapes à la ligne suivante de code ou dans une fonction, ou elle s’exécute jusqu’au curseur ou à un point d’arrêt défini, l’Allemagne passe automatiquement en mode arrêt.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle de l’exécution](../../extensibility/debugger/control-of-execution.md)
