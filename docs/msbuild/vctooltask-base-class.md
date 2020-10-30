---
title: Classe VCToolTask | Microsoft Docs
description: En savoir plus sur plusieurs paramètres que la classe de base VCToolTask ajoute aux tâches qui en héritent.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b2e45d7c672ebc2177c2bb197399133e7b077a5c
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046741"
---
# <a name="vctooltask-base-class"></a>Classe de base VCToolTask

De nombreuses tâches héritent au final de la classe <xref:Microsoft.Build.Utilities.Task> et de la classe [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Cette classe ajoute plusieurs paramètres aux tâches qui en dérivent. Ces paramètres sont répertoriés dans ce document.

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la classe de base **VCToolTask** .

|Paramètre|Description|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|Paramètre **de \<string, ToolSwitch> dictionnaire** facultatif.|
|**AdditionalOptions**|Paramètre de **chaîne** facultatif.|
|**EffectiveWorkingDirectory**|Paramètre de **chaîne** facultatif.|
|**EnableErrorListRegex**|Paramètre **booléen** facultatif.<br/><br/>La valeur par défaut est `true`.|
|**ErrorListRegex**|Paramètre **ITaskItem []** facultatif.|
|**ErrorListListExclusion**|Paramètre **ITaskItem []** facultatif.|
|**GenerateCommandLine**|Paramètre de **chaîne** facultatif.<br/><br/>Utilise les valeurs **CommandLineFormat** *format* [par défaut = CommandLineFormat.ForBuildLog] et **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default].|
|**GenerateCommandLineExceptSwitches**|Paramètre de **chaîne** facultatif.<br/><br/>Utilise les valeurs **chaîne[]** *switchesToRemove* , **CommandLineFormat** *format* [par défaut = CommandLineFormat.ForBuildLog] et **EscapeFormat** *escapeFormat* [par défaut = EscapeFormat.Default].|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)<br/>
[Tâches](../msbuild/msbuild-tasks.md)
