---
title: "AL (Assembly Linker) Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#AL"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "AL task [MSBuild]"
  - "MSBuild, AL task"
ms.assetid: 2ddefbf2-5662-4d55-99a6-ac383bf44560
caps.latest.revision: 22
caps.handback.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# AL (Assembly Linker) Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La tâche AL inclut AL.exe, outil distribué avec le [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)], dans un wrapper.  L'outil Assembly Linker sert à créer un assembly avec un manifeste à partir d'un ou de plusieurs fichiers qui sont soit des modules, soit des fichiers de ressources.  Les compilateurs et les environnements de développement offrent parfois ces fonctionnalités. Il est donc souvent inutile d'utiliser directement cette tâche.  L'outil Assembly Linker sera plus utile pour les développeurs ayant besoin de créer un seul assembly pour plusieurs fichiers composants, tels que ceux qui peuvent être générés par un développement à plusieurs langages.  Cette tâche ne combine pas les modules en un seul fichier d'assembly ; les modules individuels doivent toujours être distribués et disponibles afin que l'assembly résultant puisse être correctement chargé.  Pour plus d'informations sur AL.exe, consultez [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `AL`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AlgorithmID`|Paramètre `String` facultatif.<br /><br /> Spécifie un algorithme de hachage de tous les fichiers dans un assembly multifichier, à l'exception du fichier qui contient le manifeste d'assembly.  Pour plus d'informations, consultez la documentation de l'option `/algid` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`BaseAddress`|Paramètre `String` facultatif.<br /><br /> Spécifie l'adresse de chargement d'une DLL sur l'ordinateur de l'utilisateur au moment de l'exécution.  Le chargement des applications est plus rapide si vous spécifiez l'adresse de base des DLL, plutôt que de laisser le système d'exploitation réadresser les DLL dans l'espace de traitement.  Ce paramètre correspond à l'option \/base\[address\] dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)|  
|`CompanyName`|Paramètre `String` facultatif.<br /><br /> Spécifie une chaîne pour le champ `Company` de l'assembly.  Pour plus d'informations, consultez la documentation de l'option `/comp[any]` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Configuration`|Paramètre `String` facultatif.<br /><br /> Spécifie une chaîne pour le champ `Configuration` de l'assembly.  Pour plus d'informations, consultez la documentation de l'option `/config[uration]` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Copyright`|Paramètre `String` facultatif.<br /><br /> Spécifie une chaîne pour le champ `Copyright` de l'assembly.  Pour plus d'informations, consultez la documentation de l'option `/copy[right]` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Culture`|Paramètre `String` facultatif.<br /><br /> Spécifie la chaîne de culture à associer à l'assembly.  Pour plus d'informations, consultez la documentation de l'option `/c[ulture]` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`DelaySign`|Paramètre `Boolean` facultatif.<br /><br /> `true` pour placer uniquement la clé publique dans l'assembly ; `false` pour signer complètement l'assembly.  Pour plus d'informations, consultez la documentation de l'option `/delay[sign]` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Description`|Paramètre `String` facultatif.<br /><br /> Spécifie une chaîne pour le champ `Description` de l'assembly.  Pour plus d'informations, consultez la documentation de l'option `/descr[iption]` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`EmbedResources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` optionnel.<br /><br /> Incorpore les ressources spécifiées dans l'image qui contient le manifeste d'assembly.  Cette tâche copie le contenu du fichier de ressources dans l'image.  Les éléments passés dans ce paramètre peuvent avoir des métadonnées facultatives associées appelées `LogicalName` et `Access`.  Les métadonnées `LogicalName` sont utilisées pour spécifier l'identificateur interne de la ressource.  Les métadonnées `Access` peuvent avoir la valeur `private` pour rendre la ressource invisible à d'autres assemblys.  Pour plus d'informations, consultez la documentation de l'option `/embed[resource]` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`EvidenceFile`|Paramètre `String` facultatif.<br /><br /> Incorpore le fichier spécifié dans l'assembly avec le nom de ressource `Security.Evidence`.<br /><br /> Vous ne pouvez pas utiliser `Security.Evidence` pour les ressources classiques.  Ce paramètre correspond à l'option `/e[vidence]` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)|  
|`ExitCode`|Paramètre de sortie en lecture seule `Int32` facultatif.<br /><br /> Spécifie le code de sortie fourni par la commande exécutée.|  
|`FileVersion`|Paramètre `String` facultatif.<br /><br /> Spécifie une chaîne pour le champ `File Version` de l'assembly.  Pour plus d'informations, consultez la documentation de l'option `/fileversion` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Flags`|Paramètre `String` facultatif.<br /><br /> Spécifie une valeur pour le champ `Flags` de l'assembly.  Pour plus d'informations, consultez la documentation de l'option `/flags` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`GenerateFullPaths`|Paramètre `Boolean` facultatif.<br /><br /> Force la tâche à utiliser le chemin d'accès absolu de tout fichier signalé dans un message d'erreur.  Ce paramètre correspond à l'option `/fullpaths` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)|  
|`KeyContainer`|Paramètre `String` facultatif.<br /><br /> Spécifie un conteneur qui contient une paire de clés.  Cela signe l'assembly \(lui donne un nom fort\) en insérant une clé publique dans le manifeste d'assembly.  La tâche signe ensuite l'assembly final à l'aide la clé privée.  Pour plus d'informations, consultez la documentation de l'option `/keyn[ame]` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`KeyFile`|Paramètre `String` facultatif.<br /><br /> Spécifie un fichier qui contient une paire de clés ou juste une clé publique pour signer un assembly.  Le compilateur insère la clé publique dans le manifeste d'assembly, puis signe l'assembly final avec la clé privée.  Pour plus d'informations, consultez la documentation de l'option `/keyf[ile]` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`LinkResources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` optionnel.<br /><br /> Lie les fichiers de ressources spécifiés à un assembly.  La ressource est intégrée à l'assembly, mais le fichier n'est pas copié.  Les éléments passés dans ce paramètre peuvent être attachées à des métadonnées facultatives appelées `LogicalName`, `Target` et `Access`.  Les métadonnées `LogicalName` sont utilisées pour spécifier l'identificateur interne de la ressource.  Les métadonnées `Target` peuvent spécifier le chemin d'accès et le nom de fichier vers lesquels la tâche copie le fichier, après quoi il compile ce nouveau fichier dans l'assembly.  Les métadonnées `Access` peuvent avoir la valeur `private` pour rendre la ressource invisible à d'autres assemblys.  Pour plus d'informations, consultez la documentation de l'option `/link[resource]` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`MainEntryPoint`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom complet \(*class.method*\) de la méthode à utiliser comme point d'entrée lors de la conversion d'un module en fichier exécutable.  Ce paramètre correspond à l'option `/main` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)|  
|`OutputAssembly`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem> requis.<br /><br /> Spécifie le nom du fichier généré par cette tâche.  Ce paramètre correspond à l'option `/out` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)|  
|`Platform`|Paramètre `String` facultatif.<br /><br /> Limite les plateformes sur lesquelles ce code peut s'exécuter ; il doit s'agir de `x86`, `Itanium`, `x64`ou `anycpu`.  La valeur par défaut est `anycpu`.  Ce paramètre correspond à l'option `/platform` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)|  
|`ProductName`|Paramètre `String` facultatif.<br /><br /> Spécifie une chaîne pour le champ `Product` de l'assembly.  Pour plus d'informations, consultez la documentation de l'option `/prod[uct]` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`ProductVersion`|Paramètre `String` facultatif.<br /><br /> Spécifie une chaîne pour le champ `ProductVersion` de l'assembly.  Pour plus d'informations, consultez la documentation de l'option `/productv[ersion]` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`ResponseFiles`|Paramètre `String[]` facultatif.<br /><br /> Spécifie les fichiers réponse qui contiennent les options supplémentaires à passer à l'outil Assembly Linker.|  
|`SdkToolsPath`|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin d'accès des outils du Kit de développement logiciel, comme resgen.exe.|  
|`SourceModules`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` optionnel.<br /><br /> Un ou plusieurs modules à compiler dans un assembly.  Les modules sont répertoriés dans le manifeste d'assembly résultant et doivent toujours être distribués et disponibles pour que l'assembly puisse être chargé.  Les éléments passés dans ce paramètre peuvent posséder des métadonnées supplémentaires appelées `Target`, qui spécifient le chemin d'accès et le nom de fichier vers lesquels la tâche copie le fichier avant de compiler ce nouveau fichier dans l'assembly.  Pour plus d'informations, consultez la documentation de [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).  Ce paramètre correspond à la liste de modules passée dans Al.exe sans commutateur spécifique.|  
|`TargetType`|Paramètre `String` facultatif.<br /><br /> Spécifie le format de fichier du fichier de sortie : `library` \(bibliothèque de codes\), `exe` \(application console\) ou `win` \(application Windows\).  La valeur par défaut est `library`.  Ce paramètre correspond à l'option `/t[arget]` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)|  
|`TemplateFile`|Paramètre `String` facultatif.<br /><br /> Spécifie l'assembly à partir duquel hériter de toutes les métadonnées d'assembly, à l'exception du champ culture.  L'assembly spécifié doit avoir un nom fort.<br /><br /> Un assembly créé avec le paramètre `TemplateFile` est un assembly satellite.  Ce paramètre correspond à l'option `/template` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)|  
|`Timeout`|Paramètre `Int32` facultatif.<br /><br /> Spécifie la durée, en millisecondes, après laquelle la tâche exécutable est terminée.  La valeur par défaut est `Int.MaxValue`, indiquant qu'il n'existe aucun délai d'attente.|  
|`Title`|Paramètre `String` facultatif.<br /><br /> Spécifie une chaîne pour le champ `Title` de l'assembly.  Pour plus d'informations, consultez la documentation de l'option `/title` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`ToolPath`|Paramètre `String` facultatif.<br /><br /> Spécifie l'emplacement à partir duquel la tâche charge le fichier exécutable sous\-jacent \(Al.exe\).  Si ce paramètre n'est pas spécifié, la tâche utilise le chemin d'accès d'installation du Kit de développement logiciel qui correspond à la version de l'infrastructure exécutant [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|`Trademark`|Paramètre `String` facultatif.<br /><br /> Spécifie une chaîne pour le champ `Trademark` de l'assembly.  Pour plus d'informations, consultez la documentation de l'option `/trade[mark]` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Version`|Paramètre `String` facultatif.<br /><br /> Spécifie les informations de version concernant cet assembly.  Le format de la chaîne est *major.minor.build.revision*.  La valeur par défaut est 0.  Pour plus d'informations, consultez la documentation de l'option `/v[ersion]` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Win32Icon`|Paramètre `String` facultatif.<br /><br /> Insère un fichier .ico dans l'assembly.  Le fichier .ico donne au fichier de sortie l'apparence souhaitée dans l'Explorateur de fichiers.  Ce paramètre correspond à l'option `/win32icon` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)|  
|`Win32Resource`|Paramètre `String` facultatif.<br /><br /> Insère une ressource Win32 \(fichier .res\) dans le fichier de sortie.  Pour plus d'informations, consultez la documentation de l'option `/win32res` dans [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
  
## Notes  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.ToolTask>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## Exemple  
 L'exemple suivant crée un assembly avec les options spécifiées.  
  
```  
<AL  
    EmbedResources="@(EmbeddedResource)"  
    Culture="%(EmbeddedResource.Culture)"  
    TemplateFile="@(IntermediateAssembly)"  
    KeyContainer="$(KeyContainerName)"  
    KeyFile="$(KeyOriginatorFile)"  
    DelaySign="$(DelaySign)"  
  
    OutputAssembly=  
       "%(EmbeddedResource.Culture)\$(TargetName).resources.dll">  
  
    <Output TaskParameter="OutputAssembly"  
        ItemName="SatelliteAssemblies"/>  
</AL>  
```  
  
## Voir aussi  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Tasks](../msbuild/msbuild-tasks.md)