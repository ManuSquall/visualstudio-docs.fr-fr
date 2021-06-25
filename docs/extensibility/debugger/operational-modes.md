---
title: Modes opérationnels | Microsoft Docs
description: Découvrez les trois modes dans lesquels l’IDE peut fonctionner, en mode Design, en mode exécution et en mode arrêt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 559df92545f4c14eb0575e7ef758e73028349b76
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899106"
---
# <a name="operational-modes"></a>Modes de fonctionnement
L’IDE peut fonctionner dans trois modes, comme suit :

- [Mode création](#vsconoperationalmodesanchor1)

- [Mode d’exécution](#vsconoperationalmodesanchor2)

- [Mode arrêt](#vsconoperationalmodesanchor3)

  La façon dont vos transitions DE moteur DE débogage personnalisées entre ces modes est une décision d’implémentation vous oblige à vous familiariser avec les mécanismes de transition. Le DE peut ou ne peut pas implémenter directement ces modes. Ces modes sont en fait des modes de package de débogage qui basculent en fonction des actions de l’utilisateur ou des événements du. Par exemple, le passage du mode exécution au mode arrêt est provoqué par un événement d’arrêt à partir de la. La transition de break en mode exécution ou en mode étape est provoquée par l’utilisateur effectuant des opérations telles que STEP ou Execute. Pour plus d’informations sur les transitions, consultez [contrôle de l’exécution](../../extensibility/debugger/control-of-execution.md).

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a> Mode création
 Le mode Design est l’état non exécuté du débogage Visual Studio, ce qui vous permet de définir des fonctionnalités de débogage dans votre application.

 Seules quelques fonctionnalités de débogage sont utilisées en mode création. Un développeur peut choisir de définir des points d’arrêt ou de créer des expressions Watch. Le DE n’est jamais chargé ou appelé lorsque l’IDE est en mode Design. L’interaction avec le DE a lieu uniquement en mode exécution et en mode arrêt.

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a> Mode d’exécution
 Le mode d’exécution se produit lorsqu’un programme s’exécute dans une session de débogage dans l’IDE. L’application s’exécute jusqu’à la fin, jusqu’à ce qu’un point d’arrêt soit atteint ou jusqu’à ce qu’une exception soit levée. Lorsque l’application s’exécute jusqu’à l’arrêt, le DE passe en mode création. Lorsqu’un point d’arrêt est atteint ou qu’une exception est levée, la valeur DE passe en mode arrêt.

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a> Mode arrêt
 Le mode arrêt se produit lorsque l’exécution du programme de débogage est suspendue. Le mode arrêt offre au développeur un instantané de l’application au moment de l’arrêt et permet au développeur d’analyser l’état de l’application et de modifier le mode d’exécution de l’application. Le développeur peut afficher et modifier le code, examiner ou modifier des données, redémarrer l’application, terminer l’exécution ou poursuivre l’exécution à partir du même point.

 Le mode arrêt est entré lorsque le DE envoie un événement d’arrêt synchrone. Les événements d’arrêt synchrones, également appelés événements d’arrêt, notifient le gestionnaire de débogage de session (SDM) et l’IDE que l’application en cours de débogage a cessé d’exécuter le code. Les interfaces [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) et [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sont des exemples d’arrêt d’événements.

 Les événements d’arrêt sont poursuivis par un appel à l’une des méthodes suivantes, qui font passer le débogueur du mode arrêt au mode exécution ou en mode pas à pas :

- [Execute](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [Étape](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [Continuer](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a> Mode pas à pas
 Le mode pas à pas se produit lorsque le programme passe à la ligne de code suivante, ou à, au-dessus ou à l’extérieur d’une fonction. Une étape est exécutée en appelant l' [étape](../../extensibility/debugger/reference/idebugprocess3-step.md)de méthode. Cette méthode nécessite `DWORD` des s qui spécifient les énumérations [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) et [STEPKIND](../../extensibility/debugger/reference/stepkind.md) en tant que paramètres d’entrée.

 Quand le programme parvient à passer à la ligne de code suivante ou à une fonction, ou qu’il s’exécute sur le curseur ou sur un point d’arrêt défini, le DE passe automatiquement en mode arrêt.

## <a name="see-also"></a>Voir aussi
- [Contrôle de l’exécution](../../extensibility/debugger/control-of-execution.md)
