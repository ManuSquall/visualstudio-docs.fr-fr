---
title: MT, tâche | Microsoft Docs
description: Découvrez les paramètres et les options de ligne de commande de la tâche MSBuild MT, qui encapsule l’outil manifeste Microsoft, mt.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCManifestTool.ResourceOutputFileName
- VC.Project.VCManifestTool.SuppressDependencyElement
- VC.Project.VCManifestTool.ManifestFromManagedAssembly
- VC.Project.VCManifestTool.GenerateCategoryTags
- VC.Project.VCManifestTool.EnableDPIAwareness
- vc.task.mt
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBUILD (C++), MT task
- MT task (MSBuild (C++))
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5ce7e602c3f95766fdade297c2ee235cebba24c
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048981"
---
# <a name="mt-task"></a>MT (tâche)

Encapsule l’outil manifeste Microsoft, *mt.exe* . Pour plus d’informations, voir [mt.exe](/windows/desktop/SbsCs/mt-exe).

## <a name="parameters"></a>Paramètres

 Le tableau suivant décrit les paramètres de la tâche **MT** . La plupart des paramètres de tâche, et quelques ensembles de paramètres, correspondent à une option de ligne de commande.

> [!NOTE]
> La documentation de *mt.exe* utilise un trait **-** d’Union () comme préfixe pour les options de ligne de commande, mais cette rubrique utilise une barre oblique ( **/** ). Les deux préfixes sont acceptés.

|Paramètre|Description|
|---------------|-----------------|
|**AdditionalManifestFiles**|Paramètre **String []** facultatif.<br /><br /> Spécifie le nom d’un ou plusieurs fichiers manifestes.<br /><br /> Pour plus d’informations, voir l’option **/manifest** de [mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**AdditionalOptions**|Paramètre de **chaîne** facultatif.<br /><br /> Liste des options de ligne de commande. Par exemple,/ \<option1>  / \<option2>  / \<option#> . Utilisez ce paramètre pour spécifier des options de ligne de commande qui ne sont représentées par aucun autre paramètre de la tâche **MT** .<br /><br /> Pour plus d’informations, voir [mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**AssemblyIdentity**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie les valeurs d’attribut de l’élément **assemblyIdentity** du manifeste. Spécifiez une liste délimitée par des virgules, où le premier composant est la valeur de l' `name` attribut, suivi d’une ou plusieurs paires nom/valeur qui se présentent sous la forme, *\<attribute name> =<ATTRIBUTE_VALUE>* .<br /><br /> Pour plus d’informations, voir l’option **/identity** de [mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ComponentFileName**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le nom de la bibliothèque de liens dynamiques que vous souhaitez générer à partir des fichiers. *RGS* ou *. tlb* . Ce paramètre est obligatoire si vous spécifiez les paramètres **RegistrarScriptFile** ou **TypeLibraryFile** de la tâche MT.<br /><br /> Pour plus d’informations, voir l’option **/dll** de [mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**DependencyInformationFile**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le fichier d’informations sur les dépendances utilisé par Visual Studio pour effectuer le suivi des informations sur les dépendances de la génération pour l’outil Manifeste.|
|**EmbedManifest**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, incorpore le fichier manifeste dans l’assembly. Si `false`, crée un fichier manifeste autonome.|
|**EnableDPIAwareness**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, ajoute au manifeste des informations qui marquent l’application comme prenant en charge DPI. Écrire une application avec prise en charge DPI permet d’obtenir une interface utilisateur agréable et cohérente pour différents paramètres d’affichage en haute résolution.<br /><br /> Pour plus d’informations, voir [Haute résolution](/windows/desktop/win7devguide/high-dpi).|
|**GenerateCatalogFiles**|Paramètre `Boolean` facultatif.<br /><br /> Si `true` , génère des fichiers de définition de catalogue ( *. CDF* ).<br /><br /> Pour plus d’informations, voir l’option **/makecdfs** de [mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**GenerateCategoryTags**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, entraîne la génération d’étiquettes de catégorie. Si ce paramètre est `true`, le paramètre de tâche **ManifestFromManagedAssemblyMT** doit également être spécifié.<br /><br /> Pour plus d’informations, voir l’option **/category** de [mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**InputResourceManifests**|Paramètre de **chaîne** facultatif.<br /><br /> Entre le manifeste à partir d’une ressource de type RT_MANIFEST qui a l’identificateur spécifié. Spécifiez une ressource sous la forme \<file> [; [ #] \<resource_id> ], où le \<resource_id> paramètre facultatif est un nombre 16 bits non négatif.<br /><br /> Si aucun `resource_id` n’est spécifié, la valeur par défaut de CREATEPROCESS_MANIFEST_RESOURCE (1) est utilisée.<br /><br /> Pour plus d’informations, voir l’option **/inputresource** de [mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ManifestFromManagedAssembly**|Paramètre de **chaîne** facultatif.<br /><br /> Génère un manifeste à partir de l’assembly managé spécifié.<br /><br /> Pour plus d’informations, voir l’option **/managedassemblyname** de [mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ManifestToIgnore**|Paramètre de **chaîne** facultatif.<br /><br /> (Non utilisé.)|
|**OutputManifestFile**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le nom du manifeste de sortie. Si ce paramètre est omis et que vous n’utilisez qu’un seul manifeste, ce manifeste est modifié sur place.<br /><br /> Pour plus d’informations, voir l’option **/out** de [mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**OutputResourceManifests**|Paramètre de **chaîne** facultatif.<br /><br /> Génère le manifeste sur une ressource de type RT_MANIFEST qui a l’identificateur spécifié. La ressource se présente sous la forme \<file> [; [ #] \<resource_id> ], où le \<resource_id> paramètre facultatif est un nombre 16 bits non négatif.<br /><br /> Si aucun `resource_id` n’est spécifié, la valeur par défaut de CREATEPROCESS_MANIFEST_RESOURCE (1) est utilisée.<br /><br /> Pour plus d’informations, voir l’option **/outputresource** de [mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**RegistrarScriptFile**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le nom du fichier de script d’inscription ( *. RGS* ) à utiliser pour la prise en charge de manifeste com sans inscription.<br /><br /> Pour plus d’informations, voir l’option **/rgs** de [mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ReplacementsFile**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le fichier qui contient des valeurs pour les chaînes remplaçables dans le fichier de script d’inscription ( *. RGS* ).<br /><br /> Pour plus d’informations, voir l’option **/replacements** de [mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ResourceOutputFileName**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le fichier de ressources de sortie utilisé pour incorporer le manifeste dans la sortie du projet.|
|**Sources**|Paramètre `ITaskItem[]` facultatif.<br /><br /> Spécifie une liste des fichiers sources du manifeste, séparés par des espaces.<br /><br /> Pour plus d’informations, voir l’option **/manifest** de [mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**SuppressDependencyElement**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, génère un manifeste sans éléments de dépendance. Si ce paramètre est `true`, vous devez aussi spécifier le paramètre de tâche **ManifestFromManagedAssemblyMT** .<br /><br /> Pour plus d’informations, voir l’option **/nodependency** de [mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**SuppressStartupBanner**|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, empêche l'affichage du message de copyright et de numéro de version quand la tâche démarre.<br /><br /> Pour plus d’informations, voir l’option **/nologo** de [mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**TrackerLogDirectory**|Paramètre `String` facultatif.<br /><br /> Spécifie le répertoire intermédiaire dans lequel sont stockés les fichiers journaux de suivi de cette tâche.|
|**TypeLibraryFile**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le nom du fichier de bibliothèque de types ( *. tlb* ). Si vous spécifiez ce paramètre, spécifiez aussi le paramètre de tâche **ComponentFileNameMT** .<br /><br /> Pour plus d’informations, voir l’option **/tlb** de [mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**UpdateFileHashes**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, calcule la valeur de hachage des fichiers dans le chemin spécifié par le paramètre de tâche **UpdateFileHashesSearchPathMT** , puis met à jour la valeur de l’attribut **hash** de l’élément **file** du manifeste en utilisant la valeur calculée.<br /><br /> Pour plus d’informations, voir l’option **/hashupdate** de [mt.exe](/windows/desktop/SbsCs/mt-exe). Consultez également le paramètre **UpdateFileHashesSearchPath** dans ce tableau.|
|**UpdateFileHashesSearchPath**|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin de recherche à utiliser quand les hachages de fichier sont mis à jour. Utilisez ce paramètre avec le paramètre de tâche **UpdateFileHashesMT** .<br /><br /> Pour plus d’informations, consultez le paramètre **UpdateFileHashes** dans ce tableau.|
|**VerboseOutput**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, affiche des informations de débogage détaillées.<br /><br /> Pour plus d’informations, voir l’option **/verbose** de [mt.exe](/windows/desktop/SbsCs/mt-exe).|

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
