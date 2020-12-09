---
title: Création d’un moteur de débogage personnalisé | Microsoft Docs
description: Utilisez ces articles pour en savoir plus sur la création d’un moteur de débogage qui permet de déboguer des architectures Runtime particulières.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 673b08bf5680e04c90376c9eb3d63f6f03df9723
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914190"
---
# <a name="create-a-custom-debug-engine"></a>Créer un moteur de débogage personnalisé
Un moteur de débogage (DE) est un composant qui permet de déboguer des architectures Runtime particulières. Il n’y a généralement qu’une seule implémentation par environnement au moment DE l’exécution.

> [!NOTE]
> Bien qu’il existe des implémentations distinctes de Transact-SQL et JScript, VBScript et JScript partagent un seul DE.

 Un DE fonctionne avec l’interpréteur ou le système d’exploitation pour fournir des services de débogage tels que le contrôle d’exécution, les points d’arrêt et l’évaluation d’expression. Ces services sont implémentés par le biais des interfaces DE et peuvent entraîner la transition du débogueur entre différents modes opérationnels. Pour plus d’informations, consultez [modes opérationnels](../../extensibility/debugger/operational-modes.md).

 La création d’un DE comprend les étapes suivantes :

1. Inscrire un auprès de Visual Studio

2. Activer un programme à déboguer

3. Implémenter le contrôle d’exécution et l’évaluation d’État

4. Envoyer des événements

5. Configurer la terminaison et le détachement

## <a name="in-this-section"></a>Dans cette section
 [Inscrire un moteur de débogage personnalisé](../../extensibility/debugger/registering-a-custom-debug-engine.md) Explique les étapes nécessaires à l’inscription d’un moteur de débogage avec Visual Studio afin de pouvoir l’utiliser.

 [Activer un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) Explique qu’avant de pouvoir déboguer un programme, vous devez d’abord lancer le ou l’attacher à un programme existant.

 [Implémenter le contrôle d’exécution et l’évaluation d’État](../../extensibility/debugger/execution-control-and-state-evaluation.md) Explique pourquoi le débogage d’une application nécessite l’implémentation des fonctionnalités de contrôle d’exécution.

 [Envoyer des événements](../../extensibility/debugger/sending-events.md) Décrit la communication entre le débogueur et le en tant que modèle d’événement basé sur DCOM.

 [Configurer la terminaison et le détachement](../../extensibility/debugger/termination-and-detaching.md) Explique comment atteindre un arrêt normal, ce qui signifie qu’il n’y a aucun point d’arrêt, exception, erreur d’exécution ou boucle infinie dans l’application à déboguer.

 [Appeler les événements du débogueur](../../extensibility/debugger/calling-debugger-events.md) Documente l’ordre d’appel des événements qui se produisent dans une session de débogage.

 [Comment : déboguer un moteur de débogage personnalisé](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) Explique comment déboguer un personnalisé DE.

## <a name="see-also"></a>Voir aussi
- [Extensibilité du débogueur Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
