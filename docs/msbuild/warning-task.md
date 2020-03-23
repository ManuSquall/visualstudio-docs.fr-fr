---
title: Warning, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e95b59b4ccc0bd2df89e45512a5bdd05c027556
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631092"
---
# <a name="warning-task"></a>Avertissement (tâche)

Enregistre un avertissement durant une génération en fonction d’une instruction conditionnelle évaluée.

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche `Warning` .

| Paramètre | Description |
|---------------| - |
| `Code` | Paramètre `String` facultatif.<br /><br /> Code d’avertissement à associer à l’avertissement. |
| `File` | Paramètre `String` facultatif.<br /><br /> Spécifie le fichier approprié, le cas échéant. Si aucun fichier n’est fourni, le fichier qui contient la tâche d’avertissement (Warning) est utilisé. |
| `HelpKeyword` | Paramètre `String` facultatif.<br /><br /> Mot clé d’aide à associer à l’avertissement. |
| `Text` | Paramètre `String` facultatif.<br /><br /> Le texte d’avertissement que MSBuild enregistre si le `Condition` paramètre évalue à `true`. |

## <a name="remarks"></a>Notes 

 La `Warning` tâche permet aux projets MSBuild de vérifier la présence d’une configuration ou d’une propriété requise avant de passer à l’étape suivante de la construction.

 Si le paramètre `Condition` de la tâche `Warning` a la valeur `true`, la valeur du paramètre `Text` est journalisée et la génération se poursuit. Si aucun paramètre `Condition` n’existe, le texte de l’avertissement est journalisé. Pour plus d’informations sur la journalisation, voir [Obtenir des journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md).

 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour une liste de ces paramètres supplémentaires et leurs descriptions, voir [TaskExtension classe de base](../msbuild/taskextension-base-class.md).

## <a name="example"></a> Exemple

 L’exemple de code suivant vérifie les propriétés définies sur la ligne de commande. Si aucune propriété n’est définie, le projet déclenche un événement d’avertissement et journalise la valeur du paramètre `Text` de la tâche `Warning`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="ValidateCommandLine">
        <Warning
            Text=" The 0 property was not set on the command line."
            Condition="'$(0)' == ''" />
        <Warning
            Text=" The FREEBUILD property was not set on the command line."
            Condition="'$(FREEBUILD)' == ''" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Obtenir des journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Référence du schéma de fichier de projet](../msbuild/msbuild-project-file-schema-reference.md)
