---
title: RC, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- vc.task.rc
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- RC task (MSBuild (C++))
- MSBuild (C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13ae844759cb73de6dc7bcce6c8898c21132f9d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632912"
---
# <a name="rc-task"></a>RC (tâche)

Encapsule l’outil Compilateur de ressources Microsoft, *rc.exe*. La tâche **RC** compile des ressources, telles que des curseurs, des icônes, des images bitmap, des boîtes de dialogue et des polices, dans un fichier de ressources (*.res*). Pour plus d’informations, consultez [Compilateur de ressources](/windows/desktop/menurc/resource-compiler).

## <a name="parameters"></a>Paramètres

 Le tableau suivant décrit les paramètres de la tâche RC. La plupart des paramètres de tâche, et quelques ensembles de paramètres, correspondent à une option de ligne de commande.

|Paramètre|Description|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Paramètre **String []** facultatif.<br /><br /> Ajoute un répertoire à la liste des répertoires dans lesquels sont recherchés les fichiers include.<br /><br /> Pour plus d’informations, lisez la section relative à l’option **/I** dans [Utilisation de RC (ligne de commande RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**AdditionalOptions**|Paramètre de **chaîne** facultatif.<br /><br /> Liste d’options de ligne de commande ; par exemple,/ \<option1>  / \<option2>  / \<option#> . Utilisez ce paramètre pour spécifier des options de ligne de commande qui ne sont pas représentées par un autre paramètre de tâche **RC**.<br /><br /> Pour plus d’informations, lisez la section relative aux options dans [Utilisation de RC (ligne de commande RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Culturel**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie un ID de paramètres régionaux qui représente la culture utilisée dans les ressources.<br /><br /> Pour plus d’informations, lisez la section relative à l’option **/** dans [Utilisation de RC (ligne de commande RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**IgnoreStandardIncludePath**|Paramètre **booléen** facultatif.<br /><br /> Si `true`, empêche le compilateur de ressources de vérifier la variable d’environnement INCLUDE lorsqu’il recherche des fichiers d’en-tête ou des fichiers de ressources.<br /><br /> Pour plus d’informations, lisez la section relative à l’option **/x** dans [Utilisation de RC (ligne de commande RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**NullTerminateStrings**|Paramètre **booléen** facultatif.<br /><br /> Si `true`, termine par la valeur Null toutes les chaînes de la table de chaînes.<br /><br /> Pour plus d’informations, lisez la section relative à l’option **/n** dans [Utilisation de RC (ligne de commande RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**PreprocessorDefinitions**|Paramètre **String []** facultatif.<br /><br /> Définissez un ou plusieurs symboles de préprocesseur pour le compilateur de ressources. Spécifiez une liste de symboles de macro.<br /><br /> Pour plus d’informations, lisez la section relative à l’option **/d** dans [Utilisation de RC (ligne de commande RC)](/windows/win32/menurc/using-rc-the-rc-command-line-). Regardez également **UndefinePreprocessorDefinitions** dans ce tableau.|
|**ResourceOutputFileName**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le nom du fichier de ressources. Spécifiez un nom de fichier de ressources.<br /><br /> Pour plus d’informations, lisez la section relative à l’option **/fo** dans [Utilisation de RC (ligne de commande RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**ShowProgress**|Paramètre **booléen** facultatif.<br /><br /> Si `true`, affiche les messages qui signale la progression du compilateur.<br /><br /> Pour plus d’informations, lisez la section relative à l’option **/v** dans [Utilisation de RC (ligne de commande RC)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Source**|Paramètre `ITaskItem[]` requis.<br /><br /> Définit un tableau d’éléments de fichier source MSBuild pouvant être consommés et émis par des tâches.|
|**SuppressStartupBanner**|Paramètre **booléen** facultatif.<br /><br /> Si la valeur est `true`, empêche l'affichage du message de copyright et de numéro de version quand la tâche démarre.<br /><br /> Pour plus d’informations, tapez l’option de ligne de commande **/?**, puis regardez l’option **/nologo**.|
|**TrackerLogDirectory**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le répertoire des journaux de suivi.|
|**UndefinePreprocessorDefinitions**|Annule la définition d’un symbole du préprocesseur.<br /><br /> Pour plus d’informations, lisez la section relative à l’option **/u** dans [Utilisation de RC (ligne de commande RC)](/windows/win32/menurc/using-rc-the-rc-command-line-). Regardez également **PreprocessorDefinitions** dans ce tableau.|

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)