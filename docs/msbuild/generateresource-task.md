---
title: GenerateResource, tâche | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateResource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateResource task
- GenerateResource task [MSBuild]
ms.assetid: c0aff32f-f2cc-46f6-9c3e-a5c9f8f912b1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c830b640b3efb4e963d62402bbf68d1bc7dff0e9
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176952"
---
# <a name="generateresource-task"></a>GenerateResource (tâche)
Convertit les fichiers *.txt* et *.resx* (format de ressources XML) en fichiers *.resources* binaires du Common Language Runtime qui peuvent être incorporés dans un exécutable binaire runtime ou compilés en assemblys satellites. Cette tâche est généralement utilisée pour convertir des fichiers *.txt* ou *.resx* en fichiers *.resources*. La fonctionnalité de la tâche `GenerateResource` est similaire à [resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator).  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `GenerateResource` .  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AdditionalInputs`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient des entrées supplémentaires pour la vérification des dépendances effectuée par cette tâche. Par exemple, les fichiers projet et cibles doivent généralement être des entrées, pour que toutes les ressources soient régénérées en cas de mise à jour.|  
|`EnvironmentVariables`|Paramètre `String[]` facultatif.<br /><br /> Spécifie un tableau de paires nom-valeur de variables d’environnement qui doivent être passées au fichier *resgen.exe* généré, en plus (ou en remplacement sélectif) du bloc d’environnement normal.|  
|`ExcludedInputPaths`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie un tableau d’éléments qui indiquent les chemins à partir desquels les entrées suivies seront ignorées pendant la vérification de mise à jour.|  
|`ExecuteAsTool`|Paramètre `Boolean` facultatif.<br /><br /> Si sa valeur est `true`, exécute *tlbimp.exe* et *aximp.exe* à partir du framework cible approprié out-of-process pour générer les assemblys de wrappers nécessaires. Ce paramètre autorise le multi-ciblage de `ResolveComReferences`.|  
|`FilesWritten`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient les noms de tous les fichiers écrits sur disque. Cela comprend le fichier cache, le cas échéant. Ce paramètre est utile pour les implémentations de Clean.|  
|`MinimalRebuildFromTracking`|Paramètre `Boolean` facultatif.<br /><br /> Obtient ou définit un commutateur qui spécifie si la génération incrémentielle suivie sera utilisée. Si la valeur est `true`, la génération incrémentielle est activée ; sinon, une régénération est exécutée.|  
|`NeverLockTypeAssemblies`|Paramètre `Boolean` facultatif.<br /><br /> Récupère ou définit une valeur booléenne qui indique si un [AppDomain](/dotnet/api/system.appdomain) doit être créé pour évaluer les fichiers de ressources (*.resx*) (True) ou si un [AppDomain](/dotnet/api/system.appdomain) doit être créé uniquement quand les fichiers de ressources font référence à un assembly d’utilisateur (False).|  
|`OutputResources`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie le nom des fichiers générés, comme les fichiers *.resources*. Si vous ne spécifiez pas de nom, le nom du fichier d’entrée correspondant est utilisé et le fichier *.resources* créé est placé dans le répertoire qui contient le fichier d’entrée.|  
|`PublicClass`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, crée une classe de ressource fortement typée en tant que classe publique.|  
|`References`|Paramètre `String[]` facultatif.<br /><br /> Références à partir desquelles charger les types dans les fichiers *.resx*. Les éléments de données de fichiers *.resx* peuvent avoir un type .NET. Lors de la lecture du fichier *.resx*, il doit être résolu. En règle générale, on utilise pour cela des règles de chargement de type standard. Si vous fournissez des assemblys dans `References`, ils sont prioritaires.<br /><br /> Ce paramètre n’est pas obligatoire pour les ressources fortement typées.|  
|`SdkToolsPath`|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin des outils du SDK, comme *resgen.exe*.|  
|`Sources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les éléments à convertir. Les éléments passés à ce paramètre doivent avoir l’une des extensions de fichier suivantes :<br /><br /> -   *.txt* : spécifie l’extension d’un fichier texte à convertir. Les fichiers texte ne peuvent comporter que des ressources de chaîne.<br />-   *.resx* : spécifie l’extension d’un fichier de ressources XML à convertir.<br />-   *.restext* : spécifie le même format que *.txt*. Cette autre extension est utile si vous voulez distinguer clairement les fichiers sources qui contiennent des ressources d’autres fichiers sources dans votre processus de génération.<br />-   *.resources* : spécifie l’extension d’un fichier de ressources à convertir.|  
|`StateFile`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le chemin d’un fichier cache facultatif qui sert à accélérer la vérification des dépendances des liens dans les fichiers d’entrée *.resx*.|  
|`StronglyTypedClassName`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom de classe pour la classe de ressources fortement typée. Si vous ne spécifiez pas ce paramètre, le nom de base du fichier de ressources est utilisé.|  
|`StronglyTypedFilename`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le nom du fichier source. Si vous ne spécifiez pas ce paramètre, le nom de la classe est utilisé comme nom de base, avec une extension qui dépend du langage. Par exemple : *MyClass.cs*.|  
|`StronglyTypedLanguage`|Paramètre `String` facultatif.<br /><br /> Spécifie le langage à utiliser lors de la génération de la source de classe pour la ressource fortement typée. Ce paramètre doit correspondre exactement à l’un des langages utilisés par CodeDomProvider. Par exemple : `VB` ou `C#`.<br /><br /> En transmettant une valeur à ce paramètre, vous demandez à la tâche de générer des ressources fortement typées.|  
|`StronglyTypedManifestPrefix`|Paramètre `String` facultatif.<br /><br /> Spécifie le préfixe de manifeste ou d’espace de noms de ressources à utiliser dans la source de classe générée pour la ressource fortement typée.|  
|`StronglyTypedNamespace`|Paramètre `String` facultatif.<br /><br /> Spécifie l’espace de noms à utiliser pour la source de classe générée pour la ressource fortement typée. Si vous ne spécifiez pas ce paramètre, toutes les ressources fortement typées sont dans l’espace de noms global.|  
|`TLogReadFiles`|Paramètre en lecture seule <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient un tableau des éléments qui représentent les journaux de suivi de lecture.|  
|`TLogWriteFiles`|Paramètre en lecture seule <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient un tableau des éléments qui représentent les journaux de suivi d’écriture.|  
|`ToolArchitecture`|Paramètre <xref:System.String?displayProperty=fullName> facultatif.<br /><br /> Utilisé pour déterminer si *Tracker.exe* doit être utilisé pour générer *ResGen.exe*.<br /><br /> Doit être analysable pour un membre de l’énumération <xref:Microsoft.Build.Utilities.ExecutableType>. Si `String.Empty`, utilise une heuristique pour déterminer une architecture par défaut. Doit être analysable pour un membre de l’énumération Microsoft.Build.Utilities.ExecutableType.|  
|`TrackerFrameworkPath`|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin de l’emplacement .NET Framework approprié qui contient *FileTracker.dll*.<br /><br /> Si vous définissez ce paramètre, il incombe à l’utilisateur de s’assurer que le nombre de bits du fichier *FileTracker.dll* qu’il transmet correspond au nombre de bits du fichier *ResGen.exe* qu’il a l’intention d’utiliser. Si vous ne spécifiez pas ce paramètre, la tâche choisit l’emplacement approprié en fonction de la version actuelle du .NET Framework.|  
|`TrackerLogDirectory`|Paramètre `String` facultatif.<br /><br /> Spécifie le répertoire intermédiaire dans lequel les journaux de suivi d’exécution de cette tâche seront placés.|  
|`TrackerSdkPath`|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin de l’emplacement du SDK Windows approprié qui contient *Tracker.exe*.<br /><br /> Si vous définissez ce paramètre, il incombe à l’utilisateur de s’assurer que le nombre de bits du fichier *Tracker.exe* qu’il transmet correspond au nombre de bits du fichier *ResGen.exe* qu’il a l’intention d’utiliser. Si vous ne spécifiez pas ce paramètre, la tâche choisit l’emplacement approprié en fonction du SDK Windows actuel.|  
|`TrackFileAccess`|Paramètre <xref:System.Boolean> facultatif.<br /><br /> Si la valeur est true, le répertoire du fichier d’entrée est utilisé pour résoudre les chemins de fichiers relatifs.|  
|`UseSourcePath`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, indique que le répertoire du fichier d’entrée doit être utilisé pour résoudre les chemins de fichiers relatifs.|  
  
## <a name="remarks"></a>Notes  
 Étant donné que les fichiers *.resx* peuvent contenir des liens vers d’autres fichiers de ressources, il ne suffit pas de simplement comparer les horodatages des fichiers *.resx* et *.resources* pour savoir si les sorties sont à jour. Au lieu de cela, la tâche `GenerateResource` suit les liens figurant dans les fichiers *.resx* et vérifie aussi les horodatages des fichiers liés. Cela signifie qu’en général vous ne devez pas utiliser d’attributs `Inputs` et `Outputs` sur la cible contenant la tâche `GenerateResource`, car elle risque dans ce cas d’être ignorée alors qu’elle doit être exécutée.  
  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base TaskExtension](../msbuild/taskextension-base-class.md).  
  
 Quand vous utilisez MSBuild 4.0 pour cibler des projets .NET 3.5, la génération peut échouer sur des ressources x86. Pour contourner ce problème, vous pouvez générer la cible en tant qu’assembly AnyCPU.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la tâche `GenerateResource` pour générer des fichiers *.resources* à partir des fichiers spécifiés par la collection d’éléments `Resx`.  
  
```xml  
<GenerateResource  
    Sources="@(Resx)"  
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">  
    <Output  
        TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
 La tâche `GenerateResource` utilise les métadonnées \<LogicalName> d’un élément \<EmbeddedResource> pour nommer la ressource incorporée dans un assembly.  
  
 En supposant que l’assembly se nomme myAssembly, le code suivant génère une ressource incorporée nommée *someQualifier.someResource.resources* :  
  
```xml  
<ItemGroup>   <EmbeddedResource Include="myResource.resx">       <LogicalName>someQualifier.someResource.resources</LogicalName>   </EmbeddedResource></ItemGroup>  
```  
  
 Sans les métadonnées \<LogicalName>, la ressource se nommerait *myAssembly.myResource.resources*.  Cet exemple s’applique uniquement au processus de génération Visual Basic et Visual C#.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
