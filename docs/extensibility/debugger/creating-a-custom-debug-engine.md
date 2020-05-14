---
title: Création d’un moteur Debug personnalisé (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: a350d640fffcc6e09cf8f981c797b97071a0cacf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739041"
---
# <a name="create-a-custom-debug-engine"></a>Créer un moteur de débogé personnalisé
Un moteur de débogé (DE) est un composant qui permet de déboguer des architectures particulières de temps de course. Il n’y a généralement qu’une seule mise en œuvre DE par environnement de temps de course.

> [!NOTE]
> Bien qu’il existe des implémentations DE distinctes pour Transact-SQL et JScript, VBScript et JScript partagent un seul DE.

 Un DE travaille avec l’interprète ou le système d’opération pour fournir des services de débogage tels que le contrôle d’exécution, les points d’arrêt et l’évaluation de l’expression. Ces services sont implémentés à travers les interfaces DE et peuvent provoquer la transition du débbuggeur entre les différents modes opérationnels. Pour plus d’informations, voir [modes opérationnels](../../extensibility/debugger/operational-modes.md).

 La création d’un DE se compose des étapes suivantes :

1. Enregistrez un DE avec Visual Studio

2. Permettre la déboiffée d’un programme

3. Mettre en œuvre le contrôle d’exécution et l’évaluation de l’État

4. Envoyer des événements

5. Mettre en place la résiliation et le détachement

## <a name="in-this-section"></a>Contenu de cette section
 [Enregistrer un moteur de débogé personnalisé](../../extensibility/debugger/registering-a-custom-debug-engine.md) Explique les étapes nécessaires pour enregistrer un moteur de débogé avec Visual Studio afin qu’il puisse être utilisé.

 [Permettre la déboiffée d’un programme](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) Explique qu’avant que votre DE puisse déboiffer un programme, vous devez d’abord lancer le DE ou l’attacher à un programme existant.

 [Mettre en œuvre le contrôle d’exécution et l’évaluation de l’État](../../extensibility/debugger/execution-control-and-state-evaluation.md) Discute des raisons pour lesquelles la débogage d’une application nécessite la mise en œuvre de fonctionnalités de contrôle d’exécution.

 [Envoyer des événements](../../extensibility/debugger/sending-events.md) Décrit la communication entre le débbugger et le DE comme un modèle d’événement basé sur DCOM.

 [Mettre en place la résiliation et le détachement](../../extensibility/debugger/termination-and-detaching.md) Explique comment obtenir la résiliation normale, ce qui signifie qu’il n’y a pas de points d’arrêt, d’exceptions, d’erreurs de temps d’exécution ou de boucles infinies dans l’application à déboguer.

 [Événements de débogénaire d’appel](../../extensibility/debugger/calling-debugger-events.md) Documente l’ordre d’appel des événements qui se produisent lors d’une session de débogage.

 [Comment: Débogé d’un moteur de débogé personnalisé](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) Explique comment déboiffer un DE personnalisé.

## <a name="see-also"></a>Voir aussi
- [Visual Studio débbugger extensibility](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
