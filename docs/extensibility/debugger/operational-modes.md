---
title: Modes opérationnels (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 027152b2b2fc18b509a687220e5d963ea1b7e721
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738278"
---
# <a name="operational-modes"></a>Modes opérationnels
Il existe trois modes dans lesquels l’IDE peut fonctionner, comme suit :

- [Mode design](#vsconoperationalmodesanchor1)

- [Mode d’exécution](#vsconoperationalmodesanchor2)

- [Mode de rupture](#vsconoperationalmodesanchor3)

  La façon dont votre moteur de débogé personnalisé (DE) passe entre ces modes est une décision de mise en œuvre qui vous oblige à connaître les mécanismes de transition. Le DE peut ou non implémenter directement ces modes. Ces modes sont vraiment déboiffer les modes de paquet qui passent en fonction de l’action de l’utilisateur ou des événements de la DE. Par exemple, la transition du mode d’exécution au mode de rupture est incitée par un événement d’arrêt de la DE. La transition de la rupture au mode d’exécution ou en mode étape est incitée par l’utilisateur effectuant des opérations telles que Step ou Execute. Pour plus d’informations sur les transitions DE, voir [Contrôle de l’exécution](../../extensibility/debugger/control-of-execution.md).

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a>Mode design
 Le mode design est l’état non régrutien du débogage Visual Studio, au cours duquel vous pouvez définir des fonctionnalités de débogage dans votre application.

 Seules quelques fonctionnalités de débogage sont utilisées en mode design. Un développeur peut choisir de définir des points d’arrêt ou de créer des expressions de montre. Le DE n’est jamais chargé ou appelé pendant que l’IDE est en mode de conception. L’interaction avec le DE a lieu uniquement pendant les modes de course et de rupture.

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a>Mode d’exécution
 Le mode d’exécution se produit lorsqu’un programme s’exécute dans une session de débogage dans l’IDE. L’application s’exécute jusqu’à la résiliation, jusqu’à ce qu’un point d’arrêt soit atteint, ou jusqu’à ce qu’une exception soit lancée. Lorsque l’application s’exécute à la résiliation, le DE passe en mode de conception. Lorsqu’un point d’arrêt est atteint ou qu’une exception est lancée, le DE passe en mode de rupture.

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a>Mode pause
 Le mode de rupture se produit lorsque l’exécution du programme de débogage est suspendue. Le mode pause offre au développeur un instantané de l’application au moment de la pause et permet au développeur d’analyser l’état de l’application et de modifier la façon dont l’application s’exécutera. Le développeur peut afficher et modifier le code, examiner ou modifier des données, redémarrer l’application, mettre fin à l’exécution ou continuer l’exécution à partir du même point.

 Le mode de rupture est entré lorsque le DE envoie un événement d’arrêt synchrone. Les événements d’arrêt synchrones, également appelés événements d’arrêt, avisent le gestionnaire de débogé de session (SDM) et l’IDE que l’application en cours de débbugged a cessé d’exécuter le code. Les interfaces [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) et [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sont des exemples d’événements d’arrêt.

 Les événements d’arrêt sont poursuivis par un appel à l’une des méthodes suivantes, qui font la transition du débbugger du mode de rupture au mode d’exécution ou d’étape :

- [Exécuter](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [Étape](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [Continuer](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a>Mode étape
 Le mode étape se produit lorsque le programme passe à la ligne de code suivante, ou dans, plus ou hors d’une fonction. Une étape est exécutée en appelant la méthode [Step](../../extensibility/debugger/reference/idebugprocess3-step.md). Cette méthode `DWORD`nécessite des indices [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) et [STEPKIND](../../extensibility/debugger/reference/stepkind.md) comme paramètres d’entrée.

 Lorsque le programme passe avec succès à la ligne suivante de code ou dans une fonction, ou il s’exécute vers le curseur ou à un point d’arrêt défini, le DE passe automatiquement en mode de rupture.

## <a name="see-also"></a>Voir aussi
- [Contrôle de l’exécution](../../extensibility/debugger/control-of-execution.md)
