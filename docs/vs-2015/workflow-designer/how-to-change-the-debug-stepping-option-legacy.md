---
title: 'Procédure : Modifier l’Option d’exécution pas à pas de débogage (hérité) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5380c73b8286d492cb29f60acce3294aaac25d1f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952528"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Procédure : Modifier l’option de débogage pas à pas (héritée)
Cette rubrique décrit comment modifier l'option de débogage pas à pas pour les applications [!INCLUDE[wf](../includes/wf-md.md)] dans le [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité qui comportent des actions simultanées. Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Lorsque vous déboguez des activités héritées exécutées simultanément, tel que **ParallelActivity** ou **ConditionedActivityGroup**, vous pouvez utiliser une des deux options pour parcourir votre code.  
  
 Procédez comme suit pour modifier l'option de débogage pas à pas dans votre projet de workflow hérité.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-change-the-debug-stepping-option"></a>Pour modifier l'option de débogage pas à pas  
  
1.  Démarrez Visual Studio.  
  
2.  Ouvrez un projet de workflow hérité existant ou créez un nouveau projet qui fait appel à des activités simultanées et qui cible le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
3.  Sur le **Workflow** menu dans les anciennes [!INCLUDE[wfd2](../includes/wfd2-md.md)], pointez sur **déboguer**, puis pointez sur **Options pas à pas**.  
  
4.  Sélectionnez **Instance** ou **branche**.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de Workflows hérités](../workflow-designer/debugging-legacy-workflows.md)   
 [Options de débogage pas à pas (hérité)](../workflow-designer/debug-stepping-options-legacy.md)