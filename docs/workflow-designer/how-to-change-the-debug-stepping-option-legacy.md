---
title: "Comment : modifier l’Option d’exécution pas à pas de débogage (hérité) | Documents Microsoft"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ea687b0a08aa4697ac9f7c7b0aca875af131a561
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Procédure : modifier l'option de débogage pas à pas (héritée)
Cette rubrique décrit comment modifier l’option de débogage pas à pas pour [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] applications dans le Concepteur de flux de travail Windows hérité qui comportent des actions simultanées. Utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Lorsque vous déboguez des activités héritées exécutées simultanément, tel que **ParallelActivity** ou **ConditionedActivityGroup**, vous pouvez utiliser une des deux options pour parcourir votre code.

 Procédez comme suit pour modifier l'option de débogage pas à pas dans votre projet de workflow hérité.

## <a name="procedures"></a>Procédures

#### <a name="to-change-the-debug-stepping-option"></a>Pour modifier l'option de débogage pas à pas

1.  Démarrez Visual Studio.

2.  Ouvrez un projet de workflow hérité existant ou créez un nouveau projet qui fait appel à des activités simultanées et qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

3.  Sur le **Workflow** menu hérité [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], pointez sur **déboguer**, puis pointez sur **Options pas à pas**.

4.  Sélectionnez **Instance** ou **branche**.

## <a name="see-also"></a>Voir aussi

- [Débogage de flux de travail hérités](../workflow-designer/debugging-legacy-workflows.md)
- [Options de débogage pas à pas (hérité)](../workflow-designer/debug-stepping-options-legacy.md)