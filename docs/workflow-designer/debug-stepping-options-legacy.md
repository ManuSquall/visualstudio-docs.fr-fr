---
title: Concepteur de flux de travail - Options de débogage pas à pas (héritée)
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f46c0ab382a0e189c595e6e0f8aeb69c71814faf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="debug-stepping-options-legacy"></a>Options de débogage pas à pas (héritées)

Cette rubrique décrit comment déboguer des applications Windows Workflow Foundation (WF) qui ont des activités simultanées dans le Concepteur de flux de travail Windows hérité. Utilisez le Concepteur de flux de travail hérité lorsque vous avez besoin cibler le .NET Framework version 3.5 ou du WinFX.

Lorsque vous déboguez des activités héritées exécutées simultanément, tel que **ParallelActivity** ou **ConditionedActivityGroup**, vous pouvez utiliser une des deux options suivantes pour parcourir votre code .

-   **Branches pas à pas.** Ce mode d’exécution pas à pas vous permet de parcourir et déboguer une branche spécifique d’une activité composite, comme le **ParallelActivity** ou **ConditionalActivityGroup** activité. Lorsque vous utilisez cette option pour déboguer des activités, vous ne remarquerez aucune modification du contrôle due à l'exécution simultanée d'autres activités dans le workflow. Le débogueur parcourt uniquement les activités dans la branche sélectionnée pendant que d’autres activités peuvent s’exécuter en même temps dans le workflow. Par exemple, par défaut, la branche à l’extrême gauche dans une **ParallelActivity** activité et la première activité enfant d’un **ConditionedActivityGroup** activité sont utilisées. Si l'utilisateur souhaite déboguer toute autre branche ou toute autre activité enfant, un point d'arrêt explicite doit être placé sur cette branche ou cette activité enfant. Le pas à pas continue dans cette branche lorsque le point d’arrêt est déclenché.

-   **Exécution pas à pas d’instance.** Ce mode de pas à pas vous permet de parcourir et déboguer des activités exécutées de manière simultanée dans le workflow. Avec cette option, vous remarquerez une modification du contrôle en cas d'activités exécutées simultanément dans le workflow.

Par défaut, l'option de débogage de branches est sélectionnée et les utilisateurs peuvent alterner entre les deux options lorsqu'ils déboguent un workflow hérité.

Vous devez sélectionner l'option de débogage d'instance lors du débogage de workflows d'ordinateur d'état hérités.

## <a name="see-also"></a>Voir aussi

- [Débogage de flux de travail hérités](../workflow-designer/debugging-legacy-workflows.md)
- [Guide pratique pour modifier l’option de débogage pas à pas (hérité)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)