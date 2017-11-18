---
title: "Déboguer des Options pas à pas (hérité) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: fbdb0d481c0740310f40f6a75d8c84db765f847d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="debug-stepping-options-legacy"></a>Options de débogage pas à pas (héritées)
Cette rubrique décrit comment déboguer des applications [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] qui ont des activités simultanées dans le [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité. Utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Lorsque vous déboguez des activités héritées exécutées simultanément, tel que **ParallelActivity** ou **ConditionedActivityGroup**, vous pouvez utiliser une des deux options suivantes pour parcourir votre code .  
  
-   **Branches pas à pas.** Ce mode d’exécution pas à pas vous permet de parcourir et déboguer une branche spécifique d’une activité composite, comme le **ParallelActivity** ou **ConditionalActivityGroup** activité. Lorsque vous utilisez cette option pour déboguer des activités, vous ne remarquerez aucune modification du contrôle due à l'exécution simultanée d'autres activités dans le workflow. Le débogueur parcourt uniquement les activités dans la branche sélectionnée pendant que d'autres activités peuvent s'exécuter en même temps dans le workflow. Par exemple, par défaut, la branche à l’extrême gauche dans une **ParallelActivity** activité et la première activité enfant d’un **ConditionedActivityGroup** activité sont utilisées. Si l'utilisateur souhaite déboguer toute autre branche ou toute autre activité enfant, un point d'arrêt explicite doit être placé sur cette branche ou cette activité enfant. Le pas à pas continue dans cette branche lorsque le point d’arrêt est déclenché.  
  
-   **Exécution pas à pas d’instance.** Ce mode de pas à pas vous permet de parcourir et déboguer des activités exécutées de manière simultanée dans le workflow. Avec cette option, vous remarquerez une modification du contrôle en cas d'activités exécutées simultanément dans le workflow.  
  
 Par défaut, l'option de débogage de branches est sélectionnée et les utilisateurs peuvent alterner entre les deux options lorsqu'ils déboguent un workflow hérité.  
  
 Vous devez sélectionner l'option de débogage d'instance lors du débogage de workflows d'ordinateur d'état hérités.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de Workflows hérités](../workflow-designer/debugging-legacy-workflows.md)   
 [Guide pratique pour modifier l’option de débogage pas à pas (hérité)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)