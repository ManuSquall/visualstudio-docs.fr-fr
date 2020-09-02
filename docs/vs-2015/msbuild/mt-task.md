---
title: MT, tâche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
- MSBUILD (Visual C++), MT task
- MT task (MSBuild (Visual C++))
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d705bff368e813bdd2c7fe2b60ba9ada8f679bbf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845969"
---
# <a name="mt-task"></a>MT, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Inclut l’outil Manifeste (mt.exe) de Microsoft dans un wrapper. Pour plus d’informations, consultez « Mt.exe » sur le site web [MSDN](https://msdn.microsoft.com/).  
  
## <a name="parameters"></a>Paramètres  
 Le tableau suivant décrit les paramètres de la tâche **MT**. La plupart des paramètres de tâche, et quelques ensembles de paramètres, correspondent à une option de ligne de commande.  
  
> [!NOTE]
> La documentation de mt.exe utilise un trait **-** d’Union () comme préfixe pour les options de ligne de commande, mais cette rubrique utilise une barre oblique ( **/** ). Les deux préfixes sont acceptés.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**AdditionalManifestFiles**|Paramètre **String []** facultatif.<br /><br /> Spécifie le nom d’un ou plusieurs fichiers manifestes.<br /><br /> Pour plus d’informations, consultez l’option **/manifest** dans « Mt.exe » sur le site web [MSDN](https://msdn.microsoft.com/).|  
|**AdditionalOptions**|Paramètre de **chaîne** facultatif.<br /><br /> Liste des options de ligne de commande. Par exemple, «*/option1/option2/option #*». Utilisez ce paramètre pour spécifier des options de ligne de commande qui ne sont représentées par aucun autre paramètre de la tâche **MT**.<br /><br /> Pour plus d’informations, consultez « Mt.exe » sur le site web [MSDN](https://msdn.microsoft.com/).|  
|**AssemblyIdentity**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie les valeurs d’attribut de l’élément **assemblyIdentity** du manifeste. Spécifiez une liste délimitée par des virgules, où le premier composant est la valeur de l' `name` attribut, suivi d’une ou plusieurs paires nom/valeur qui se présentent sous la forme, * \<attribute name> =<ATTRIBUTE_VALUE>*.<br /><br /> Pour plus d’informations, consultez l’option **/identity** dans « Mt.exe » sur le site web [MSDN](https://msdn.microsoft.com/).|  
|**ComponentFileName**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le nom de la bibliothèque de liens dynamiques que vous prévoyez de générer à partir des fichiers .rgs ou .tlb. Ce paramètre est obligatoire si vous spécifiez les paramètres **RegistrarScriptFile** ou **TypeLibraryFile** de la tâche MT.<br /><br /> Pour plus d’informations, consultez l’option **/dll** dans « Mt.exe » sur le site web [MSDN](https://msdn.microsoft.com/).|  
|**DependencyInformationFile**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le fichier d’informations sur les dépendances utilisé par Visual Studio pour effectuer le suivi des informations sur les dépendances de la génération pour l’outil Manifeste.|  
|**EmbedManifest**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, incorpore le fichier manifeste dans l’assembly. Si `false`, crée un fichier manifeste autonome.|  
|**EnableDPIAwareness**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, ajoute au manifeste des informations qui marquent l’application comme prenant en charge DPI. Écrire une application avec prise en charge DPI permet d’obtenir une interface utilisateur agréable et cohérente pour différents paramètres d’affichage en haute résolution.<br /><br /> Pour plus d’informations, consultez « High DPI » sur le site web [MSDN](https://msdn.microsoft.com/).|  
|**GenerateCatalogFiles**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, génère des fichiers de définition de catalogue (.cdf).<br /><br /> Pour plus d’informations, consultez l’option **/makecdfs** dans « Mt.exe » sur le site web [MSDN](https://msdn.microsoft.com/).|  
|**GenerateCategoryTags**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, entraîne la génération d’étiquettes de catégorie. Si ce paramètre est `true`, le paramètre de tâche **ManifestFromManagedAssemblyMT** doit également être spécifié.<br /><br /> Pour plus d’informations, consultez l’option **/category** dans « Mt.exe » sur le site web [MSDN](https://msdn.microsoft.com/).|  
|**InputResourceManifests**|Paramètre de **chaîne** facultatif.<br /><br /> Entre le manifeste à partir d’une ressource de type RT_MANIFEST qui a l’identificateur spécifié. Spécifiez une ressource sous la forme, _ \<file> [_**;** _[_ **#** _] <resource_id>]_, où le `resource_id` paramètre facultatif est un nombre 16 bits non négatif.<br /><br /> Si aucun `resource_id` n’est spécifié, la valeur par défaut de CREATEPROCESS_MANIFEST_RESOURCE (1) est utilisée.<br /><br /> Pour plus d’informations, consultez l’option **/inputresource** dans « Mt.exe » sur le site web [MSDN](https://msdn.microsoft.com/).|  
|**ManifestFromManagedAssembly**|Paramètre de **chaîne** facultatif.<br /><br /> Génère un manifeste à partir de l’assembly managé spécifié.<br /><br /> Pour plus d’informations, consultez l’option **/managedassemblyname** dans « Mt.exe » sur le site web [MSDN](https://msdn.microsoft.com/).|  
|**ManifestToIgnore**|Paramètre de **chaîne** facultatif.<br /><br /> (Non utilisé.)|  
|**OutputManifestFile**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le nom du manifeste de sortie. Si ce paramètre est omis et que vous n’utilisez qu’un seul manifeste, ce manifeste est modifié sur place.<br /><br /> Pour plus d’informations, consultez l’option **/out** dans « Mt.exe » sur le site web [MSDN](https://msdn.microsoft.com/).|  
|**OutputResourceManifests**|Paramètre de **chaîne** facultatif.<br /><br /> Génère le manifeste sur une ressource de type RT_MANIFEST qui a l’identificateur spécifié. La ressource se présente sous la forme, _ \<file> [_**;** _[_ **#** _] <resource_id>]_, où le `resource_id` paramètre facultatif est un nombre 16 bits non négatif.<br /><br /> Si aucun `resource_id` n’est spécifié, la valeur par défaut de CREATEPROCESS_MANIFEST_RESOURCE (1) est utilisée.<br /><br /> Pour plus d’informations, consultez l’option **/outputresource** dans « Mt.exe » sur le site web [MSDN](https://msdn.microsoft.com/).|  
|**RegistrarScriptFile**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le nom du fichier de script d’inscription (.rgs) à utiliser pour la prise en charge du manifeste COM sans inscription.<br /><br /> Pour plus d’informations, consultez l’option **/rgs** dans « Mt.exe » sur le site web [MSDN](https://msdn.microsoft.com/).|  
|**ReplacementsFile**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le fichier qui contient des valeurs pour les chaînes remplaçables du fichier de script d’inscription (.rgs).<br /><br /> Pour plus d’informations, consultez l’option **/replacements** dans « Mt.exe » sur le site web [MSDN](https://msdn.microsoft.com/).|  
|**ResourceOutputFileName**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le fichier de ressources de sortie utilisé pour incorporer le manifeste dans la sortie du projet.|  
|**Sources**|Paramètre `ITaskItem[]` facultatif.<br /><br /> Spécifie une liste des fichiers sources du manifeste, séparés par des espaces.<br /><br /> Pour plus d’informations, consultez l’option **/manifest** dans « Mt.exe » sur le site web [MSDN](https://msdn.microsoft.com/).|  
|**SuppressDependencyElement**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, génère un manifeste sans éléments de dépendance. Si ce paramètre est `true`, vous devez aussi spécifier le paramètre de tâche **ManifestFromManagedAssemblyMT**.<br /><br /> Pour plus d’informations, consultez l’option **/nodependency** dans « Mt.exe » sur le site web [MSDN](https://msdn.microsoft.com/).|  
|**SuppressStartupBanner**|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, empêche l'affichage du message de copyright et de numéro de version quand la tâche démarre.<br /><br /> Pour plus d’informations, consultez l’option **/nologo** dans « Mt.exe » sur le site web [MSDN](https://msdn.microsoft.com/).|  
|**TrackerLogDirectory**|Paramètre `String` facultatif.<br /><br /> Spécifie le répertoire intermédiaire dans lequel sont stockés les fichiers journaux de suivi de cette tâche.|  
|**TypeLibraryFile**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le nom du fichier de bibliothèque de types (.tlb). Si vous spécifiez ce paramètre, spécifiez aussi le paramètre de tâche **ComponentFileNameMT**.<br /><br /> Pour plus d’informations, consultez l’option **/tlb** dans « Mt.exe » sur le site web [MSDN](https://msdn.microsoft.com/).|  
|**UpdateFileHashes**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, calcule la valeur de hachage des fichiers dans le chemin spécifié par le paramètre de tâche **UpdateFileHashesSearchPathMT**, puis met à jour la valeur de l’attribut **hash** de l’élément **file** du manifeste en utilisant la valeur calculée.<br /><br /> Pour plus d’informations, consultez l’option **/hashupdate** dans « Mt.exe » sur le site web [MSDN](https://msdn.microsoft.com/). Consultez également le paramètre **UpdateFileHashesSearchPath** dans ce tableau.|  
|**UpdateFileHashesSearchPath**|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin de recherche à utiliser quand les hachages de fichier sont mis à jour. Utilisez ce paramètre avec le paramètre de tâche **UpdateFileHashesMT**.<br /><br /> Pour plus d’informations, consultez le paramètre **UpdateFileHashes** dans ce tableau.|  
|**VerboseOutput**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, affiche des informations de débogage détaillées.<br /><br /> Pour plus d’informations, consultez l’option **/verbose** dans « Mt.exe » sur le site web [MSDN](https://msdn.microsoft.com/).|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de tâche](../msbuild/msbuild-task-reference.md)
