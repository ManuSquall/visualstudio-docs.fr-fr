---
title: Création d’un moteur de débogage personnalisé | Microsoft Docs
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
ms.openlocfilehash: 241bc016d8a64905951bffef07ba425f1351a727
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903577"
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

## <a name="in-this-section"></a>Contenu de cette section
 [Inscrire un moteur de débogage personnalisé](../../extensibility/debugger/registering-a-custom-debug-engine.md) Explique les étapes nécessaires à l’inscription d’un moteur de débogage avec Visual Studio afin de pouvoir l’utiliser.

 [Activer un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) Explique qu’avant de pouvoir déboguer un programme, vous devez d’abord lancer le ou l’attacher à un programme existant.

 [Implémenter le contrôle d’exécution et l’évaluation d’État](../../extensibility/debugger/execution-control-and-state-evaluation.md) Explique pourquoi le débogage d’une application nécessite l’implémentation des fonctionnalités de contrôle d’exécution.

 [Envoyer des événements](../../extensibility/debugger/sending-events.md) Décrit la communication entre le débogueur et le en tant que modèle d’événement basé sur DCOM.

 [Configurer la terminaison et le détachement](../../extensibility/debugger/termination-and-detaching.md) Explique comment atteindre un arrêt normal, ce qui signifie qu’il n’y a aucun point d’arrêt, exception, erreur d’exécution ou boucle infinie dans l’application à déboguer.

 [Appeler les événements du débogueur](../../extensibility/debugger/calling-debugger-events.md) Documente l’ordre d’appel des événements qui se produisent dans une session de débogage.

 [Comment : déboguer un moteur de débogage personnalisé](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) Explique comment déboguer un personnalisé DE.

## <a name="see-also"></a>Voir aussi
- [Extensibilité du débogueur Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
