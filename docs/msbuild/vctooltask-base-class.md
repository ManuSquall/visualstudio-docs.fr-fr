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
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 7bdad856a6ea0ec6cca8292bc3095f51c500bcb1
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58515252"
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