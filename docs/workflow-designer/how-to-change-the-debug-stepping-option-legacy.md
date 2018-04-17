---
title: 'Comment : modifier l’Option d’exécution pas à pas de débogage (hérité) | Documents Microsoft'
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aedb8e738dc2e6ca2b066dd9a2cd42e332bbd8be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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