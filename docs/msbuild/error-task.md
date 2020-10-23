---
title: Tâche Error | Microsoft Docs
description: Utilisez la tâche d’erreur MSBuild pour arrêter une génération et consigner une erreur en fonction d’une instruction conditionnelle évaluée.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Error
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Error task [MSBuild]
- MSBuild, Error task
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2b451f9c3074af7d621576336ea3bf0e05ebea3
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436647"
---
# <a name="error-task"></a>Erreur (tâche)

Arrête une génération et enregistre une erreur en fonction d’une instruction conditionnelle évaluée.

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la tâche `Error` .

| Paramètre | Description |
|---------------| - |
| `Code` | Paramètre `String` facultatif.<br /><br /> Code d’erreur à associer à l’erreur. |
| `File` | Paramètre `String` facultatif.<br /><br /> Nom du fichier qui contient l’erreur. Si aucun nom de fichier n’est fourni, le fichier contenant la tâche Error est utilisé. |
| `HelpKeyword` | Paramètre `String` facultatif.<br /><br /> Mot clé d’aide à associer à l’erreur. |
| `Text` | Paramètre `String` facultatif.<br /><br /> Texte d’erreur que MSBuild enregistre si le `Condition` paramètre a la valeur `true` . |

## <a name="remarks"></a>Remarques

La `Error` tâche permet aux projets MSBuild d’émettre du texte d’erreur dans les journaux et d’arrêter l’exécution de la génération.

Si le paramètre `Condition` a la valeur `true`, la génération est arrêtée, et une erreur est enregistrée. Si un paramètre `Condition` n’existe pas, l’erreur est enregistrée, et l’exécution de la génération s’arrête. Pour plus d’informations sur la journalisation, consultez [Obtention de journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md).

En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemple

L’exemple de code suivant vérifie que toutes les propriétés requises sont définies. Si elles ne le sont pas, le projet déclenche un événement d’erreur et enregistre la valeur du paramètre `Text` de la tâche `Error`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="ValidateCommandLine">
        <Error
            Text=" The 0 property must be set on the command line."
            Condition="'$(0)' == ''" />
        <Error
            Text="The FREEBUILD property must be set on the command line."
            Condition="'$(FREEBUILD)' == ''" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Obtenir des journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md)
