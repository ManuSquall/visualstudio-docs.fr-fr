---
title: Exec, tâche | Microsoft Docs
description: En savoir plus sur l’utilisation de la tâche MSBuild Exec pour exécuter un programme ou une commande spécifique à l’aide des arguments spécifiés.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Exec
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, Exec task
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c3b89e074a4c67e8d16a07eb48431ebe1ade694f
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106083566"
---
# <a name="exec-task"></a>Exec (tâche)

Exécute la commande ou le programme spécifié en utilisant les arguments spécifiés.

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la tâche `Exec`.

|Paramètre|Description|
|---------------|-----------------|
|`Command`|Paramètre `String` requis.<br /><br /> Commande(s) à exécuter. Il peut s’agir de commandes système, par exemple attrib, ou d’un fichier exécutable, comme *program.exe*, *runprogram.bat* ou *setup.msi*.<br /><br /> Ce paramètre peut contenir plusieurs lignes de commandes. Vous pouvez également placer plusieurs commandes dans un fichier de commandes et l’exécuter à l’aide de ce paramètre.|
|`ConsoleOutput`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Chaque sortie d’élément est une ligne de la sortie standard ou du flux d’erreur standard émise par l’outil. Celle-ci est uniquement capturée si `ConsoleToMsBuild` a la valeur `true`.|
|`ConsoleToMsBuild`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche capture l’erreur standard et la sortie standard de l’outil pour les rendre disponibles dans le paramètre de sortie `ConsoleOutput`.<br /><br />Par défaut : `false`.|
|`CustomErrorRegularExpression`|Paramètre `String` facultatif.<br /><br /> Spécifie une expression régulière utilisée pour détecter les lignes d’erreur dans la sortie de l’outil. C’est utile pour les outils qui produisent une sortie à la mise en forme inhabituelle.<br /><br />Par défaut : `null` (aucun traitement personnalisé).|
|`CustomWarningRegularExpression`|Paramètre `String` facultatif.<br /><br /> Spécifie une expression régulière utilisée pour détecter les lignes d’avertissement dans la sortie de l’outil. C’est utile pour les outils qui produisent une sortie à la mise en forme inhabituelle.<br /><br />Par défaut : `null` (aucun traitement personnalisé).|
|`EchoOff`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche n’émet pas la forme développée de `Command` dans le journal MSBuild.<br /><br />Par défaut : `false`.|
|`ExitCode`|Paramètre en lecture seule de sortie `Int32` facultatif.<br /><br /> Spécifie le code de sortie fourni par la commande exécutée, sauf que si la tâche a enregistré des erreurs, mais que le processus a un code de sortie égal à 0 (succès), `ExitCode` a la valeur-1.|
|`IgnoreExitCode`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche ignore le code de sortie fourni par la commande exécutée. Sinon, la tâche retourne `false` si la commande exécutée retourne un code de sortie différent de zéro.<br /><br />Par défaut : `false`.|
|`IgnoreStandardErrorWarningFormat`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `false`, sélectionne des lignes dans la sortie qui correspondent au format d’erreur/avertissement standard, et les enregistre en tant qu’erreurs/avertissements. Si la valeur est `true`, désactiver ce comportement.<br /><br />Par défaut : `false`.|
|`Outputs`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient les éléments de sortie de la tâche. La tâche `Exec` ne les définit pas elle-même. Au lieu de cela, vous pouvez les fournir comme si elle les définissait, pour qu’ils puissent être utilisés ultérieurement dans le projet.|
|`StdErrEncoding`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie l’encodage du flux d’erreurs standard de tâche capturé. La valeur par défaut est l’encodage de sortie de la console actuelle.|
|`StdOutEncoding`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie l’encodage du flux de sortie standard de tâche capturé. La valeur par défaut est l’encodage de sortie de la console actuelle.|
|`UseUtf8Encoding`|Paramètre `String` facultatif.<br /><br /> Spécifie s’il faut utiliser la page de codes UTF8 lors du traitement de la ligne de commande pour les commandes exécutées. Les valeurs valides sont `Always`, `Never` ou `Detect`. La valeur par défaut est `Detect` , ce qui signifie utiliser la page de codes UTF8 uniquement lorsque des caractères non ANSI sont présents.|
|`WorkingDirectory`|Paramètre `String` facultatif.<br /><br /> Spécifie le répertoire dans lequel la commande sera exécutée.<br /><br />Par défaut : le répertoire de travail actif du projet.|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="remarks"></a>Notes

Cette tâche est utile quand une tâche MSBuild spécifique pour le travail que vous souhaitez effectuer n’est pas disponible. Toutefois, la tâche `Exec`, contrairement à une tâche plus spécifique, ne peut pas effectuer de traitement ou d’opérations conditionnelles supplémentaires en fonction du résultat de l’outil ou de la commande exécutée.

La tâche `Exec` appelle *cmd.exe* au lieu d’appeler directement un processus.

## <a name="example"></a>Exemple

L’exemple suivant utilise la tâche `Exec` pour exécuter une commande.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Binaries Include="*.dll;*.exe"/>
    </ItemGroup>

    <Target Name="SetACL">
        <!-- set security on binaries-->
        <Exec Command="echo y| cacls %(Binaries.Identity) /G everyone:R"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
