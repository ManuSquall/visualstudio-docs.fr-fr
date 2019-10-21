---
title: Options de débogage pas à pas (hérité) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 443cbac0ea9d74c61f24d6714162ec08e2906a62
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656877"
---
# <a name="debug-stepping-options-legacy"></a>Options de débogage pas à pas (héritées)
Cette rubrique décrit comment déboguer des applications [!INCLUDE[wf](../includes/wf-md.md)] qui ont des activités simultanées dans le [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité. Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Lorsque vous déboguez des activités héritées qui ont une exécution simultanée, telle que **ParallelActivity** ou **ConditionedActivityGroup**, vous pouvez utiliser l’une des deux options suivantes pour parcourir votre code pas à pas.

- **Exécution pas à pas de la branche.** Ce mode d’exécution pas à pas vous permet de parcourir et déboguer une branche particulière d’une activité composite, telle que **ParallelActivity** ou l’activité **ConditionalActivityGroup** . Lorsque vous utilisez cette option pour déboguer des activités, vous ne remarquerez aucune modification du contrôle due à l'exécution simultanée d'autres activités dans le workflow. Le débogueur parcourt uniquement les activités dans la branche sélectionnée pendant que d'autres activités peuvent s'exécuter en même temps dans le workflow. Par exemple, par défaut, la branche la plus à gauche dans une activité **ParallelActivity** et la première activité enfant d’une activité **ConditionedActivityGroup** sont utilisées pour l’exécution pas à pas. Si l'utilisateur souhaite déboguer toute autre branche ou toute autre activité enfant, un point d'arrêt explicite doit être placé sur cette branche ou cette activité enfant. Le pas à pas continue dans cette branche lorsque le point d'arrêt est déclenché.

- **Exécution pas à pas de l’instance.** Ce mode de pas à pas vous permet de parcourir et déboguer des activités exécutées de manière simultanée dans le workflow. Avec cette option, vous remarquerez une modification du contrôle en cas d'activités exécutées simultanément dans le workflow.

  Par défaut, l’option de débogage de branches est sélectionnée et les utilisateurs peuvent alterner entre les deux options lorsqu’ils déboguent un workflow hérité.

  Vous devez sélectionner l'option de débogage d'instance lors du débogage de workflows d'ordinateur d'état hérités.

## <a name="see-also"></a>Voir aussi
 [Débogage des flux de travail hérités](../workflow-designer/debugging-legacy-workflows.md) [Comment : modifier l’option de débogage pas à pas (héritée)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)