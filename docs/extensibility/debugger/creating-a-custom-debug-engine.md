---
title: Créer une personnalisée moteur de débogage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5273270905c99b565fe4fd455e9c5c505af9c878
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711096"
---
# <a name="create-a-custom-debug-engine"></a>Créer un moteur de débogage personnalisé
Un moteur de débogage (dé) est un composant qui permet le débogage d’architectures d’exécution particulières. Il est généralement qu’une seule implémentation DE chaque environnement d’exécution.

> [!NOTE]
>  Bien qu’il existe des implémentations DE distinctes pour Transact-SQL et JScript, VBScript et JScript partagent un seul DE.

 Un DE fonctionne avec le système d’interpréteur ou opération pour fournir ces services de débogage en tant que l’exécution du contrôle des points d’arrêt, évaluation et expression. Ces services sont implémentés via les interfaces DE et peuvent entraîner le débogueur à la transition entre les différents modes de fonctionnement. Pour plus d’informations, consultez [les modes de fonctionnement](../../extensibility/debugger/operational-modes.md).

 Création d’un dé se compose des étapes suivantes :

1.  Inscrire un dé avec Visual Studio

2.  Activer un programme à déboguer

3.  Implémenter l’évaluation de contrôle et l’état d’exécution

4.  Envoyer des événements

5.  Configurer d’arrêt et détachement

## <a name="in-this-section"></a>Dans cette section
 [Inscrire un moteur de débogage personnalisé](../../extensibility/debugger/registering-a-custom-debug-engine.md) explique les étapes nécessaires pour inscrire un moteur de débogage avec Visual Studio afin qu’il peut être utilisé.

 [Activer un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) explique qu’avant votre dé peut déboguer un programme, vous devez tout d’abord lancer la DE ou attacher à un programme existant.

 [Implémenter l’évaluation de contrôle et l’état d’exécution](../../extensibility/debugger/execution-control-and-state-evaluation.md) décrit pourquoi déboguer une application nécessite l’implémentation des fonctionnalités de contrôle d’exécution.

 [Envoyer des événements](../../extensibility/debugger/sending-events.md) décrit la communication entre le débogueur et de la DE comme un modèle d’événement basé sur DCOM.

 [Configurer d’arrêt et détachement](../../extensibility/debugger/termination-and-detaching.md) explique comment réaliser une fin normale, ce qui signifie qu’il n’y a aucun des points d’arrêt, les exceptions, les erreurs d’exécution ou les boucles infinies dans l’application à déboguer.

 [Appeler des événements de débogueur](../../extensibility/debugger/calling-debugger-events.md) documente l’ordre d’appel des événements qui se produisent dans une session de débogage.

 [Guide pratique pour Déboguer un moteur de débogage personnalisé](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) explique comment déboguer un dé personnalisé.

## <a name="see-also"></a>Voir aussi
- [Extensibilité du débogueur Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)