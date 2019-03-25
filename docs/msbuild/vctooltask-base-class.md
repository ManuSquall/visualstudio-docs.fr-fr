---
title: Classe VCToolTask | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: mikeblome
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: 4c7cc3490735dbd9ac43cd43555ec673cc3afccd
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070446"
---
# <a name="vctooltask-base-class"></a>Classe de base VCToolTask

De nombreuses tâches héritent au final de la classe <xref:Microsoft.Build.Utilities.Task> et de la classe [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Cette classe ajoute plusieurs paramètres aux tâches qui en dérivent. Ces paramètres sont répertoriés dans ce document.

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la classe de base **VCToolTask**.

|Paramètre|Description|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|Paramètre **Dictionary\<chaîne, ToolSwitch>** facultatif.|
|**AdditionalOptions**|Paramètre de **chaîne** facultatif.|
|**EffectiveWorkingDirectory**|Paramètre de **chaîne** facultatif.|
|**EnableErrorListRegex**|Paramètre **booléen** facultatif.<br/><br/>La valeur par défaut est `true`.|
|**ErrorListRegex**|Paramètre **ITaskItem[]** facultatif.|
|**ErrorListListExclusion**|Paramètre **ITaskItem[]** facultatif.|
|**GenerateCommandLine**|Paramètre de **chaîne** facultatif.<br/><br/>Utilise les valeurs **CommandLineFormat** *format* [par défaut = CommandLineFormat.ForBuildLog] et **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default].|
|**GenerateCommandLineExceptSwitches**|Paramètre de **chaîne** facultatif.<br/><br/>Utilise les valeurs **chaîne[]** *switchesToRemove*, **CommandLineFormat** *format* [par défaut = CommandLineFormat.ForBuildLog] et **EscapeFormat** *escapeFormat* [par défaut = EscapeFormat.Default].|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)<br/>
[Tâches](../msbuild/msbuild-tasks.md)