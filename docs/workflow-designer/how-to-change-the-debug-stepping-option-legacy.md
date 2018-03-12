---
title: "Comment : modifier l’Option d’exécution pas à pas de débogage (hérité) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: bc92b5babe53b249fc66d93adbc0d69e6f7cf0e3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Procédure : modifier l'option de débogage pas à pas (héritée)
Cette rubrique décrit comment modifier l'option de débogage pas à pas pour les applications [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] dans le [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité qui comportent des actions simultanées. Utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Lorsque vous déboguez des activités héritées exécutées simultanément, tel que **ParallelActivity** ou **ConditionedActivityGroup**, vous pouvez utiliser une des deux options pour parcourir votre code.  
  
 Procédez comme suit pour modifier l'option de débogage pas à pas dans votre projet de workflow hérité.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-change-the-debug-stepping-option"></a>Pour modifier l'option de débogage pas à pas  
  
1.  Démarrez Visual Studio.  
  
2.  Ouvrez un projet de workflow hérité existant ou créez un nouveau projet qui fait appel à des activités simultanées et qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
3.  Sur le **Workflow** menu hérité [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], pointez sur **déboguer**, puis pointez sur **Options pas à pas**.  
  
4.  Sélectionnez **Instance** ou **branche**.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de Workflows hérités](../workflow-designer/debugging-legacy-workflows.md)   
 [Options de débogage pas à pas (hérité)](../workflow-designer/debug-stepping-options-legacy.md)