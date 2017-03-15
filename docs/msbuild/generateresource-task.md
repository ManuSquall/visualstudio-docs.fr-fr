---
title: "GenerateResource Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GenerateResource"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, GenerateResource task"
  - "GenerateResource task [MSBuild]"
ms.assetid: c0aff32f-f2cc-46f6-9c3e-a5c9f8f912b1
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GenerateResource Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Effectue la conversion entre des fichiers texte et .resx \(format de ressources XML\) et des fichiers .resources binaires du Common Language Runtime qui peuvent être incorporés dans un exécutable binaire runtime ou compilés en assemblys satellites.  Cette tâche est généralement utilisée pour convertir des fichiers .txt ou .resx en fichiers .resource.  La tâche `GenerateResource` est similaire, d'un point de vue fonctionnel, à [resgen.exe](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md).  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `GenerateResource`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AdditionalInputs`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient des entrées supplémentaires pour la vérification des dépendances que la tâche exécute.  Par exemple, les fichiers projet et cibles doivent généralement correspondre à des entrées pour garantir la régénération de toutes les ressources en cas de mise à jour de ces fichiers.|  
|`EnvironmentVariables`|Paramètre `String[]` facultatif.<br /><br /> Spécifie un tableau de paires nom\-valeur de variables d'environnement qui doivent être passées au fichier resgen.exe généré, en plus du bloc environnement normal ou en remplacement de celui\-ci.|  
|`ExcludedInputPaths`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie un tableau des éléments qui spécifient les chemins d'accès pour lesquels les entrées suivies seront ignorées pendant la vérification de mise à jour.|  
|`ExecuteAsTool`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, exécute tlbimp.exe et aximp.exe à partir de la version cible du .NET Framework appropriée hors processus pour générer les assemblys de wrappers nécessaires.  Ce paramètre permet le multi\-ciblage de `ResolveComReferences`.|  
|`FilesWritten`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient les noms de tous les fichiers écrits sur le disque.  Cela inclut le fichier cache, le cas échéant.  Ce paramètre est utile pour les implémentations de Clean.|  
|`MinimalRebuildFromTracking`|Paramètre `Boolean` facultatif.<br /><br /> Obtient ou définit un commutateur qui spécifie si la build incrémentielle suivie sera utilisée.  Si la valeur est `true`, la build incrémentielle est activée ; sinon, une régénération est exécutée.|  
|`NeverLockTypeAssemblies`|Paramètre `Boolean` facultatif.<br /><br /> Spécifie le nom des fichiers générés, par exemple des fichiers .resources.  Si vous ne spécifiez pas de nom, le nom du fichier d'entrée correspondant est utilisé et le fichier .resources créé est placé dans le répertoire qui contient le fichier d'entrée.|  
|`OutputResources`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie le nom des fichiers générés, par exemple des fichiers .resources.  Si vous ne spécifiez pas de nom, le nom du fichier d'entrée correspondant est utilisé et le fichier .resources créé est placé dans le répertoire qui contient le fichier d'entrée.|  
|`PublicClass`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, crée un type de ressources fortement typé comme classe public.|  
|`References`|Paramètre `String[]` facultatif.<br /><br /> Références à partir desquelles charger les types dans des fichiers .resx.  Les éléments de donnée des fichiers .resx peuvent avoir un type .NET.  Lors de la lecture du fichier .resx, il doit être résolu.  En général, il est possible de le résoudre à l'aide de règles de chargement de type standard.  Si vous fournissez des assemblys dans `References`, ils sont prioritaires.<br /><br /> Ce paramètre n'est pas obligatoire pour les ressources fortement typées.|  
|`SdkToolsPath`|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin d'accès des outils du Kit de développement logiciel, comme resgen.exe.|  
|`Sources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les éléments à convertir.  Les éléments passés à ce paramètre doivent avoir l'une des extensions de fichier suivantes :<br /><br /> -   `.txt`: Spécifie l'extension d'un fichier texte à convertir.  Les fichiers .txt ne peuvent comporter que des ressources de type chaîne.<br />-   `.resx`: Spécifie l'extension d'un fichier de ressources XML à convertir.<br />-   `.restext`: Spécifie le même format que .txt.  Cette autre extension est utile si vous souhaitez établir une distinction précise entre les fichiers sources qui contiennent des ressources et d'autres fichiers sources dans votre processus de génération.<br />-   `.resources`: Spécifie l'extension d'un fichier de ressources à convertir.|  
|`StateFile`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le chemin d'accès à un fichier cache facultatif qui est utilisé pour accélérer le contrôle de dépendance des liens dans les fichiers d'entrée .resx.|  
|`StronglyTypedClassName`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom de classe pour la classe de ressources fortement typées.  Si ce paramètre n'est pas spécifié, le nom de base du fichier de ressources est utilisé.|  
|`StronglyTypedFilename`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le nom de fichier du fichier source.  Si ce paramètre n'est pas spécifié, le nom de la classe est utilisé comme nom de fichier de base, avec une extension différente en fonction du langage.  Par exemple : `MyClass.cs`.|  
|`StronglyTypedLanguage`|Paramètre `String` facultatif.<br /><br /> Spécifie le langage à utiliser lors de la génération de la source de classe pour la ressource fortement typée.  Ce paramètre doit correspondre exactement à l'un des langages utilisé par CodeDomProvider.  Par exemple : `VB` ou `C#`.<br /><br /> En passant une valeur à ce paramètre, vous indiquez à la tâche de générer des ressources fortement typées.|  
|`StronglyTypedManifestPrefix`|Paramètre `String` facultatif.<br /><br /> Spécifie le préfixe de manifeste ou d'espace de noms de ressource à utiliser dans la source de classe générée pour la ressource fortement typée.|  
|`StronglyTypedNamespace`|Paramètre `String` facultatif.<br /><br /> Spécifie l'espace de noms à utiliser pour la source de classe générée pour la ressource fortement typée.  Si ce paramètre n'est pas spécifié, toutes les ressources fortement typées sont dans l'espace de noms global.|  
|`TLogReadFiles`|Paramètre en lecture seule <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient un tableau des éléments qui représentent les journaux de suivi de lecture.|  
|`TLogWriteFiles`|Paramètre en lecture seule <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Obtient un tableau des éléments qui représentent les journaux de suivi d'écriture.|  
|`ToolArchitecture`|Paramètre [String](assetId:///String?qualifyHint=False&autoUpgrade=True) facultatif.<br /><br /> Utilisé pour déterminer si Tracker.exe doit être utilisé pour générer ResGen.exe.<br /><br /> Cet élément doit être analysable pour un membre de l'énumération <xref:Microsoft.Build.Utilities.ExecutableType>.  Si la valeur est `String.Empty`, une heuristique est utilisée pour déterminer une architecture par défaut.  Cet élément doit être analysable pour un membre de l'énumération Microsoft.Build.Utilities.ExecutableType.|  
|`TrackerFrameworkPath`|Paramètre assetId:///String?qualifyHint=False&autoUpgrade=True facultatif.<br /><br /> Spécifie le chemin d'accès à l'emplacement .NET Framework approprié qui contient FileTracker.dll.<br /><br /> En cas de définition, l'utilisateur assume la responsabilité de veiller à ce que le nombre de bits du fichier FileTracker.dll qu'il passe corresponde au nombre de bits de ResGen.exe qu'il prévoit d'utiliser.  S'il n'est pas défini, la tâche choisit l'emplacement approprié en fonction de la version actuelle du .NET Framework.|  
|`TrackerLogDirectory`|Paramètre assetId:///String?qualifyHint=False&autoUpgrade=True facultatif.<br /><br /> Spécifie le répertoire intermédiaire dans lequel les journaux de suivi de l'exécution de cette tâche seront placés.|  
|`TrackerSdkPath`|Paramètre assetId:///String?qualifyHint=False&autoUpgrade=True facultatif.<br /><br /> Spécifie le chemin d'accès à l'emplacement approprié du Kit de développement logiciel Windows qui contient Tracker.exe.<br /><br /> En cas de définition, l'utilisateur assume la responsabilité de veiller à ce que le nombre de bits de Tracker.exe qu'il passe corresponde au nombre de bits de ResGen.exe qu'il prévoit d'utiliser.  S'il n'est pas défini, la tâche choisit l'emplacement approprié en fonction du Kit de développement logiciel Windows actuel.|  
|`TrackFileAccess`|Paramètre [Boolean](assetId:///Boolean?qualifyHint=False&autoUpgrade=True) facultatif.<br /><br /> Si la valeur est true, le répertoire du fichier d'entrée est utilisé pour résoudre les chemins d'accès de fichier relatifs.|  
|`UseSourcePath`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, indique que le répertoire du fichier d'entrée doit être utilisé pour résoudre des chemins d'accès de fichier relatifs.|  
  
## Notes  
 Dans la mesure où les fichiers .resx peuvent contenir des liens vers d'autres fichiers de ressources, il ne suffit pas de comparer simplement des horodatages de fichiers .resx et .resource pour voir si les sorties sont à jour.  Au lieu de cela, la tâche `GenerateResource` suit les liens figurant dans les fichiers .resx et vérifie aussi les horodatages des fichiers liés.  Cela signifie que vous ne devez généralement pas utiliser les attributs `Inputs` et `Outputs` sur la cible contenant la tâche `GenerateResource`. En effet, il est possible qu'elle soit ignorée alors qu'elle doit être en réalité exécutée.  
  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
 Lorsque vous utilisez MSBuild 4.0 pour cibler les projets .NET 3.5, la build peut échouer sur les ressources x86.  Pour contourner ce problème, vous pouvez créer la cible comme un assembly AnyCPU.  
  
## Exemple  
 L'exemple suivant utilise la tâche `GenerateResource` pour générer des fichiers .resources à partir des fichiers spécifiés par la collection d'éléments `Resx`.  
  
```  
<GenerateResource  
    Sources="@(Resx)"  
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">  
    <Output  
        TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
 La tâche `GenerateResource` utilise les métadonnées \<LogicalName\> d'un élément \<EmbeddedResource\> pour nommer la ressource incorporée dans un assembly.  
  
 Supposant que l'assembly est nommé myAssembly, le code suivant génère une ressource incorporée nommée someQualifier.someResource.resources :  
  
```  
<ItemGroup>   <EmbeddedResource Include="myResource.resx">       <LogicalName>someQualifier.someResource.resources</LogicalName>   </EmbeddedResource></ItemGroup>  
```  
  
 Sans métadonnées \<LogicalName\>, la ressource serait nommée myAssembly.myResource.resources.  Cet exemple s'applique uniquement au processus de génération Visual Basic et Visual C\#.  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)