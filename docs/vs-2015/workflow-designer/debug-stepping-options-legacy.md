---
title: Options pas à pas (hérité) de débogage | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b1f0761ba750146ce7f8cc52e6992dae689f7779
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938511"
---
# <a name="debug-stepping-options-legacy"></a>Options de débogage pas à pas (héritées)
Cette rubrique décrit comment déboguer des applications [!INCLUDE[wf](../includes/wf-md.md)] qui ont des activités simultanées dans le [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité. Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Lorsque vous déboguez des activités héritées exécutées simultanément, tel que **ParallelActivity** ou **ConditionedActivityGroup**, vous pouvez utiliser une des deux options suivantes permettent de parcourir votre code .  
  
- **Branches pas à pas.** Ce mode d’exécution pas à pas vous permet de parcourir et déboguer une branche spécifique d’une activité composite, comme le **ParallelActivity** ou **ConditionalActivityGroup** activité. Lorsque vous utilisez cette option pour déboguer des activités, vous ne remarquerez aucune modification du contrôle due à l'exécution simultanée d'autres activités dans le workflow. Le débogueur parcourt uniquement les activités dans la branche sélectionnée pendant que d'autres activités peuvent s'exécuter en même temps dans le workflow. Par exemple, par défaut, la branche la plus à gauche dans un **ParallelActivity** activité et la première activité enfant d’un **ConditionedActivityGroup** activité sont utilisées pour l’exécution pas à pas. Si l'utilisateur souhaite déboguer toute autre branche ou toute autre activité enfant, un point d'arrêt explicite doit être placé sur cette branche ou cette activité enfant. Le pas à pas continue dans cette branche lorsque le point d'arrêt est déclenché.  
  
- **Instances pas à pas.** Ce mode de pas à pas vous permet de parcourir et déboguer des activités exécutées de manière simultanée dans le workflow. Avec cette option, vous remarquerez une modification du contrôle en cas d'activités exécutées simultanément dans le workflow.  
  
  Par défaut, l’option de débogage de branches est sélectionnée et les utilisateurs peuvent alterner entre les deux options lorsqu’ils déboguent un workflow hérité.  
  
  Vous devez sélectionner l'option de débogage d'instance lors du débogage de workflows d'ordinateur d'état hérités.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de Workflows hérités](../workflow-designer/debugging-legacy-workflows.md)   
 [Guide pratique pour modifier l’option de débogage pas à pas (héritée)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)