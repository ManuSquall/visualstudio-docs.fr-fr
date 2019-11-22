---
title: RC, tâche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
- RC task (MSBuild (Visual C++))
- MSBuild (Visual C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ea44b7b98cce9bcb634217f504ea1f0529a2cf15
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298968"
---
# <a name="rc-task"></a>RC, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Encapsule l’outil Compilateur de ressources Microsoft Windows (rc.exe). La tâche **RC** compile des ressources, telles que des curseurs, des icônes, des images bitmap, des boîtes de dialogue et des polices, dans un fichier de ressources (.res). Pour plus d’informations, consultez « Compilateur de ressources » sur le site web [MSDN](https://go.microsoft.com/fwlink/?LinkId=737).  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche RCtask. La plupart des paramètres de tâche, et quelques ensembles de paramètres, correspondent à une option de ligne de commande.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|Paramètre **String[]** facultatif.<br /><br /> Ajoute un répertoire à la liste des répertoires dans lesquels sont recherchés les fichiers include.<br /><br /> Pour plus d’informations, lisez la section relative à l’option **/I** dans [Utilisation de RC (ligne de commande RC)](https://go.microsoft.com/fwlink/?LinkId=155730) sur le site web MSDN.|  
|**AdditionalOptions**|Paramètre **String** facultatif.<br /><br /> Liste d’options de ligne de commande, par exemple, **"** _/option1 /option2 /option#_ ". Utilisez ce paramètre pour spécifier des options de ligne de commande qui ne sont pas représentées par un autre paramètre de tâche **RC**.<br /><br /> Pour plus d’informations, lisez la section relative aux options dans [Utilisation de RC (ligne de commande RC)](https://go.microsoft.com/fwlink/?LinkId=155730) sur le site web MSDN.|  
|**Culture**|Paramètre **String** facultatif.<br /><br /> Spécifie un ID de paramètres régionaux qui représente la culture utilisée dans les ressources.<br /><br /> Pour plus d’informations, lisez la section relative à l’option **/l** dans [Utilisation de RC (ligne de commande RC)](https://go.microsoft.com/fwlink/?LinkId=155730) sur le site web MSDN.|  
|**IgnoreStandardIncludePath**|Paramètre **Boolean** facultatif.<br /><br /> Si `true`, empêche le compilateur de ressources de vérifier la variable d’environnement INCLUDE lorsqu’il recherche des fichiers d’en-tête ou des fichiers de ressources.<br /><br /> Pour plus d’informations, lisez la section relative à l’option **/x** dans [Utilisation de RC (ligne de commande RC)](https://go.microsoft.com/fwlink/?LinkId=155730) sur le site web MSDN.|  
|**NullTerminateStrings**|Paramètre **Boolean** facultatif.<br /><br /> Si `true`, termine par la valeur Null toutes les chaînes de la table de chaînes.<br /><br /> Pour plus d’informations, lisez la section relative à l’option **/n** dans [Utilisation de RC (ligne de commande RC)](https://go.microsoft.com/fwlink/?LinkId=155730) sur le site web MSDN.|  
|**PreprocessorDefinitions**|Paramètre **String[]** facultatif.<br /><br /> Définissez un ou plusieurs symboles de préprocesseur pour le compilateur de ressources. Spécifiez une liste de symboles de macro.<br /><br /> Pour plus d’informations, lisez la section relative à l’option **/d** dans [Utilisation de RC (ligne de commande RC)](https://go.microsoft.com/fwlink/?LinkId=155730) sur le site web MSDN. Regardez également **UndefinePreprocessorDefinitions** dans ce tableau.|  
|**ResourceOutputFileName**|Paramètre **String** facultatif.<br /><br /> Spécifie le nom du fichier de ressources. Spécifiez un nom de fichier de ressources.<br /><br /> Pour plus d’informations, lisez la section relative à l’option **/fo** dans [Utilisation de RC (ligne de commande RC)](https://go.microsoft.com/fwlink/?LinkId=155730) sur le site web MSDN.|  
|**ShowProgress**|Paramètre **Boolean** facultatif.<br /><br /> Si `true`, affiche les messages qui signale la progression du compilateur.<br /><br /> Pour plus d’informations, lisez la section relative à l’option **/v** dans [Utilisation de RC (ligne de commande RC)](https://go.microsoft.com/fwlink/?LinkId=155730) sur le site web MSDN.|  
|**Source**|Paramètre `ITaskItem[]` requis.<br /><br /> Définit un tableau d’éléments de fichier source MSBuild pouvant être consommés et émis par des tâches.|  
|**SuppressStartupBanner**|Paramètre **Boolean** facultatif.<br /><br /> Si la valeur est `true`, empêche l'affichage du message de copyright et de numéro de version quand la tâche démarre.<br /><br /> Pour plus d’informations, tapez l’option de ligne de commande **/?** , puis regardez l’option **/nologo**.|  
|**TrackerLogDirectory**|Paramètre **String** facultatif.<br /><br /> Spécifie le répertoire des journaux de suivi.|  
|**UndefinePreprocessorDefinitions**|Annule la définition d’un symbole du préprocesseur.<br /><br /> Pour plus d’informations, lisez la section relative à l’option **/u** dans [Utilisation de RC (ligne de commande RC)](https://go.microsoft.com/fwlink/?LinkId=155730) sur le site web MSDN. Regardez également **PreprocessorDefinitions** dans ce tableau.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="see-also"></a>Voir aussi  
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)
