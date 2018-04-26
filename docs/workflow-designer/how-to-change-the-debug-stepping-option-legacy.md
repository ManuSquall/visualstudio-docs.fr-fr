---
title: 'Le Concepteur de flux de travail - Comment : modifier l’Option d’exécution pas à pas de débogage (hérité)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
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
ms.openlocfilehash: 31047cedd4e8772b9ebab4ef238a8fe32bc07663
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Procédure : modifier l'option de débogage pas à pas (héritée)

Cette rubrique décrit comment modifier le débogage pas à pas d’option pour les applications de Windows Workflow Foundation (WF) dans le Concepteur de flux de travail Windows hérité qui comportent des actions simultanées. Utilisez le Concepteur de flux de travail hérité lorsque vous avez besoin cibler le .NET Framework version 3.5 ou du WinFX.

Lorsque vous déboguez des activités héritées exécutées simultanément, tel que **ParallelActivity** ou **ConditionedActivityGroup**, vous pouvez utiliser une des deux options pour parcourir votre code.

Procédez comme suit pour modifier l'option de débogage pas à pas dans votre projet de workflow hérité.

## <a name="procedures"></a>Procédures

### <a name="to-change-the-debug-stepping-option"></a>Pour modifier l'option de débogage pas à pas

1.  Démarrez Visual Studio.

2.  Ouvrez un projet de workflow hérité existant ou créer un nouveau projet qui utilise des activités simultanées et qui cible le .NET Framework version 3.5 ou le WinFX.

3.  Sur le **Workflow** menu dans le Concepteur de flux de travail hérité, pointez sur **déboguer**, puis pointez sur **Options pas à pas**.

4.  Sélectionnez **Instance** ou **branche**.

## <a name="see-also"></a>Voir aussi

- [Débogage de flux de travail hérités](../workflow-designer/debugging-legacy-workflows.md)
- [Options de débogage pas à pas (hérité)](../workflow-designer/debug-stepping-options-legacy.md)