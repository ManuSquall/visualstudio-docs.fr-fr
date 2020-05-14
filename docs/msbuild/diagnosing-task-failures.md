---
title: Diagnostiquer les échecs de tâches (fr) Microsoft Docs
ms.date: 09/25/2019
ms.topic: troubleshooting
f1_keywords:
- MSBuild.ToolTask.ToolCommandFailed
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89dcb8bddf2c92406ad5eff952d1f4050d7f9262
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593276"
---
# <a name="diagnosing-task-failures"></a>Diagnostic des échecs de tâches

`MSB6006`est émis lorsqu’une <xref:Microsoft.Build.Utilities.ToolTask>classe dérivée exécute un processus d’outil qui renvoie un code de sortie non zéro si la tâche n’a pas enregistré une erreur plus spécifique.

## <a name="identifying-the-failing-task"></a>Identifier la tâche défaillante

Lorsque vous rencontrez une erreur de tâche, la première étape consiste à identifier la tâche qui échoue.

Le texte de l’erreur spécifie le nom de l’outil (soit un nom ami fourni par la mise en œuvre de <xref:Microsoft.Build.Utilities.ToolTask.ToolName> la tâche ou le nom de l’exécutable) et le code de sortie numérique. Par exemple, dans

```text
error MSB6006: "custom tool" exited with code 1.
```

Le nom `custom tool` de l’outil `1`est et le code de sortie est .

### <a name="command-line-builds"></a>Constructions de la ligne de commandement

Si la version a été configurée pour inclure un résumé (la valeur par défaut), le résumé ressemblera à ceci :

```text
Build FAILED.

"S:\MSB6006_demo\MSB6006_demo.csproj" (default target) (1) ->
(InvokeToolTask target) ->
  S:\MSB6006_demo\MSB6006_demo.csproj(19,5): error MSB6006: "custom tool" exited with code 1.
```

Ce résultat indique que l’erreur s’est produite dans `S:\MSB6006_demo\MSB6006_demo.csproj`une tâche `InvokeToolTask`définie sur `S:\MSB6006_demo\MSB6006_demo.csproj`la ligne 19 du fichier , dans une cible nommée , dans le projet .

### <a name="in-visual-studio"></a>Dans Visual Studio

Les mêmes informations sont disponibles dans la `Project` `File`liste `Line`d’erreurs Visual Studio dans les colonnes , , et .

## <a name="finding-more-failure-information"></a>Trouver plus d’informations sur l’échec

Cette erreur est émise lorsque la tâche n’a pas enregistré une erreur spécifique. L’omission de enregistrer une erreur est souvent parce que la tâche n’est pas configurée pour comprendre le format d’erreur émis par l’outil qu’il appelle.

Les outils bien élevés émettent généralement des informations contextuelles ou d’erreur sur leur flux de sortie ou d’erreur standard, et les tâches capturent et enregistrent ces informations par défaut. Regardez les entrées de journal avant que l’erreur ne se produise pour plus d’informations. La réinserment de la construction avec un niveau de journal plus élevé peut être nécessaire pour préserver ces informations.

## <a name="next-steps"></a>Étapes suivantes

Espérons que le contexte supplémentaire ou les erreurs identifiées dans l’enregistrement révèlent la cause profonde du problème.

Si elles ne le font pas, vous devrez peut-être réduire les causes potentielles en examinant les propriétés et les éléments qui sont des intrants à la tâche défaillante.
