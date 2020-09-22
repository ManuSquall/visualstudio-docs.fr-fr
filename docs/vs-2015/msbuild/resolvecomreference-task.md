---
title: ResolveCOMReference, tâche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveCOMReference task
- ResolveCOMReference task [MSBuild]
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fc9ca34d8b8afc01787db594ffba5a1a36ec190e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839874"
---
# <a name="resolvecomreference-task"></a>ResolveComReference, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Prend une liste d’un ou plusieurs noms de bibliothèques de types ou de fichiers .tlb et résout ces bibliothèques de types aux emplacements sur le disque.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `ResolveCOMReference` .  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`DelaySign`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, place la clé publique dans l’assembly. Si la valeur est `false`, signe complètement l’assembly.|  
|`EnvironmentVariables`|Paramètre `String[]` facultatif.<br /><br /> Tableau de paires de variables d'environnement, séparées par un signe égal. Ces variables sont passées aux fichiers tlbimp.exe et aximp.exe générés en plus ou en remplacement sélectif du bloc d’environnement normal.|  
|`ExecuteAsTool`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, exécute tlbimp.exe et aximp.exe à partir du framework cible approprié out-of-process pour générer les assemblys de wrappers nécessaires. Ce paramètre permet le multiciblage.|  
|`IncludeVersionInInteropName`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la version de la typelib sera incluse dans le nom du wrapper. La valeur par défaut est `false`.|  
|`KeyContainer`|Paramètre `String` facultatif.<br /><br /> Spécifie un conteneur qui contient une paire de clés<br /><br /> publique/privée.|  
|`KeyFile`|Paramètre `String` facultatif.<br /><br /> Spécifie un élément qui contient une paire de clés<br /><br /> publique/privée.|  
|`NoClassMembers`|Paramètre `Boolean` facultatif.|  
|`ResolvedAssemblyReferences`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie les références d’assembly résolues.|  
|`ResolvedFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie les fichiers avec leur nom complet sur le disque qui correspondent aux emplacements physiques des bibliothèques de types fournies comme entrée pour cette tâche.|  
|`ResolvedModules`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.|  
|`SdkToolsPath`|Paramètre [String](<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) facultatif.<br /><br /> Si `ExecuteAsTool` a la valeur `true`, ce paramètre doit être défini sur le chemin des outils du SDK de la version du framework ciblée.|  
|`StateFile`|Facultatif <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> paramètre.<br /><br /> Spécifie le fichier cache pour les horodateurs de composant COM. S’il n’est pas présent, chaque exécution régénère tous les wrappers.|  
|`TargetFrameworkVersion`|Facultatif <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> paramètre.<br /><br /> Spécifie la version du framework cible du projet.<br /><br /> La valeur par défaut est `String.Empty`. ce qui signifie qu’il n’existe pas de filtrage pour une référence basée sur le framework cible.|  
|`TargetProcessorArchitecture`|Facultatif <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> paramètre.<br /><br /> Spécifie l’architecture de processeur cible préférée. Passé à l’indicateur /machine de tlbimp.exe après traduction.<br /><br /> La valeur du paramètre doit être un membre de <xref:Microsoft.Build.Utilities.ProcessorArchitecture>.|  
|`TypeLibFiles`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie le chemin du fichier de bibliothèque de types vers les références COM. Les éléments inclus dans ce paramètre peuvent contenir des métadonnées d’élément. Pour plus d’informations, consultez la section « Métadonnées d’élément TypeLibFiles » ci-dessous.|  
|`TypeLibNames`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie les noms de bibliothèques de types à résoudre. Les éléments inclus dans ce paramètre doivent contenir certaines métadonnées d’élément. Pour plus d’informations, consultez la section « Métadonnées d’élément TypeLibNames » ci-dessous.|  
|`WrapperOutputDirectory`|Paramètre `String` facultatif.<br /><br /> Emplacement sur le disque où se trouve l’assembly d’interopérabilité généré. Si ces métadonnées d’élément ne sont pas spécifiée, la tâche utilise le chemin absolu du répertoire où se trouve le fichier projet.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="typelibnames-item-metadata"></a>Métadonnées d’élément TypeLibNames  
 Le tableau suivant décrit les métadonnées d’élément disponibles pour les éléments passés au paramètre `TypeLibNames`.  
  
|Métadonnées|Description|  
|--------------|-----------------|  
|`GUID`|Métadonnées d’élément obligatoires.<br /><br /> GUID de la bibliothèque de types. Si ces métadonnées d’élément ne sont pas spécifiées, la tâche échoue.|  
|`VersionMajor`|Métadonnées d’élément obligatoires.<br /><br /> Version principale de la bibliothèque de types. Si ces métadonnées d’élément ne sont pas spécifiées, la tâche échoue.|  
|`VersionMinor`|Métadonnées d’élément obligatoires.<br /><br /> Version secondaire de la bibliothèque de types. Si ces métadonnées d’élément ne sont pas spécifiées, la tâche échoue.|  
|`LocaleIdentifier`|Métadonnées d’élément facultatives.<br /><br /> Identificateur de paramètres régionaux (LCID) pour la bibliothèque de types. Ceci est spécifié sous la forme d’une valeur sur 32 bits qui identifie la langue préférée par un utilisateur, une région ou une application. Si ces métadonnées d’élément ne sont pas spécifiées, la tâche utilise « 0 » comme identificateur de paramètres régionaux par défaut.|  
|`WrapperTool`|Métadonnées d’élément facultatives.<br /><br /> Spécifie l’outil wrapper utilisé pour générer le wrapper d’assembly pour cette bibliothèque de types. Si ces métadonnées d’élément ne sont pas spécifiées, la tâche utilise « tlbimp » comme outil wrapper par défaut. Les choix disponibles (leur casse n’est pas prise en compte) sont :<br /><br /> -   `Primary` : utilisez cet outil wrapper quand vous voulez utiliser un assembly PIA (Primary Interop Assembly) déjà généré pour le composant COM. Quand vous utilisez cet outil wrapper, ne spécifiez pas un répertoire de sortie du wrapper, car cela provoquerait l’échec de la tâche.<br />-   `TLBImp` : utilisez cet outil wrapper quand vous voulez générer un assembly d’interopérabilité pour le composant COM.<br />-   `AXImp` : utilisez cet outil wrapper quand vous voulez générer un assembly d’interopérabilité pour un contrôle ActiveX.|  
  
## <a name="typelibfiles-item-metadata"></a>Métadonnées d’élément TypeLibFiles  
 Le tableau suivant décrit les métadonnées d’élément disponibles pour les éléments passés au paramètre `TypeLibFiles`.  
  
|Métadonnées|Description|  
|--------------|-----------------|  
|`WrapperTool`|Métadonnées d’élément facultatives.<br /><br /> Spécifie l’outil wrapper utilisé pour générer le wrapper d’assembly pour cette bibliothèque de types. Si ces métadonnées d’élément ne sont pas spécifiées, la tâche utilise « tlbimp » comme outil wrapper par défaut. Les choix disponibles (leur casse n’est pas prise en compte) sont :<br /><br /> -   `Primary` : utilisez cet outil wrapper quand vous voulez utiliser un assembly PIA (Primary Interop Assembly) déjà généré pour le composant COM. Quand vous utilisez cet outil wrapper, ne spécifiez pas un répertoire de sortie du wrapper, car cela provoquerait l’échec de la tâche.<br />-   `TLBImp` : utilisez cet outil wrapper quand vous voulez générer un assembly d’interopérabilité pour le composant COM.<br />-   `AXImp` : utilisez cet outil wrapper quand vous voulez générer un assembly d’interopérabilité pour un contrôle ActiveX.|  
  
> [!NOTE]
> Plus vous fournissez d’informations pour identifier de façon univoque une bibliothèque de types, plus grande est la possibilité que la tâche aboutisse au fichier correct sur le disque.  
  
## <a name="remarks"></a>Remarques  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Task, classe de base](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Décrites](../msbuild/msbuild-tasks.md)   
 [Référence de tâche](../msbuild/msbuild-task-reference.md)
