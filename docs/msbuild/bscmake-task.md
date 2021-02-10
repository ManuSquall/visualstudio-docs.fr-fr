---
title: BscMake, tâche | Microsoft Docs
description: En savoir plus sur BscMake, qui a inclus l’outil Microsoft Browse information Maintenance Utility bscmake.exe. L’IDE de Visual Studio n’utilise plus BscMake.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), tasks
- BscMake task (MSBuild (C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ceda15402b3588e407388d71140b73f571c03b24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964925"
---
# <a name="bscmake-task"></a>BscMake, tâche

> [!IMPORTANT]
> BscMake n’est plus utilisé par l’IDE Visual Studio. Depuis Visual Studio 2008, les informations de consultation sont stockées automatiquement dans un fichier *.sdf* dans le dossier *Solution*.

 Encapsule l’outil Microsoft Browse Information Maintenance Utility (*bscmake.exe*).  L’outil *bscmake.exe* génère un fichier d’informations de consultation (*.bsc*) à partir des fichiers browser sources (*.sbr*) qui sont créés lors de la compilation. Utilisez **l’Explorateur d’objets** pour consulter un fichier *.bsc*. Pour plus d’informations, consultez [Informations de référence sur BSCMAKE](/cpp/build/reference/bscmake-reference).

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche **BscMake**. La plupart des paramètres de tâche correspondent à une option de ligne de commande.

|Paramètre|Description|
|---------------|-----------------|
|**AdditionalOptions**|Paramètre de **chaîne** facultatif.<br /><br /> Liste des options comme indiqué sur la ligne de commande. Par exemple,/ \<option1>  / \<option2>  / \<option#> . Utilisez ce paramètre pour spécifier des options qui ne sont pas représentées par un autre paramètre de tâche **BscMake**.<br /><br /> Pour plus d’informations, consultez les options dans [Options BSCMAKE](/cpp/build/reference/bscmake-options).|
|**OutputFile**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie un nom de fichier qui remplace le nom du fichier de sortie par défaut.<br /><br /> Pour plus d’informations, consultez l’option **/o** dans [Options BSCMAKE](/cpp/build/reference/bscmake-options).|
|**PreserveSBR**|Paramètre **booléen** facultatif.<br /><br /> Si la valeur est `true`, force une génération non incrémentielle. Une build non incrémentielle complète se produit quand bien même il existe un fichier *.bsc*, et empêche les fichiers *.sbr* d’être tronqués.<br /><br /> Pour plus d’informations, consultez l’option **/n** dans [Options BSCMAKE](/cpp/build/reference/bscmake-options).|
|**Sources**|Paramètre **ITaskItem []** facultatif.<br /><br /> Définit un tableau d’éléments de fichier source MSBuild pouvant être consommés et émis par des tâches.|
|**SuppressStartupBanner**|Paramètre **booléen** facultatif.<br /><br /> Si la valeur est `true`, empêche l'affichage du message de copyright et de numéro de version quand la tâche démarre.<br /><br /> Pour plus d’informations, consultez l’option **/NOLOGO** dans [Options BSCMAKE](/cpp/build/reference/bscmake-options).|
|**TrackerLogDirectory**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le répertoire du journal de Tracker.|

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
