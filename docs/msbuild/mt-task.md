---
title: "MT Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCManifestTool.ResourceOutputFileName"
  - "VC.Project.VCManifestTool.SuppressDependencyElement"
  - "VC.Project.VCManifestTool.ManifestFromManagedAssembly"
  - "VC.Project.VCManifestTool.GenerateCategoryTags"
  - "VC.Project.VCManifestTool.EnableDPIAwareness"
  - "vc.task.mt"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBUILD (Visual C++), MT task"
  - "MT task (MSBuild (Visual C++))"
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# MT Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Encapsule l'Outil Manifeste de Microsoft, mt.exe.  Pour plus d'informations, consultez « Mt.exe » sur le site Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche **MT**.  La plupart des paramètres de tâche, et quelques jeux de paramètres, correspondent à une option de ligne de commande.  
  
> [!NOTE]
>  La documentation mt.exe utilise un trait d'union \(**\-**\) comme préfixe pour les options de ligne de commande, mais cette rubrique utilise une barre oblique \(**\/**\).  L'un ou l'autre préfixe est acceptable.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**AdditionalManifestFiles**|Paramètre **String\[\]** facultatif.<br /><br /> Spécifie le nom d'un ou de plusieurs fichiers manifeste.<br /><br /> Pour plus d'informations, consultez l'option **\/manifest** dans « Mt.exe » sur le site Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**AdditionalOptions**|Paramètre **String** facultatif.<br /><br /> Liste d'options de ligne de commande.  Par exemple, "*\/option1 \/option2 \/option\#*".  Utilisez ce paramètre pour spécifier des options de ligne de commande qui ne sont pas représentées par un  autre paramètre de tâche **MT**.<br /><br /> Pour plus d'informations, consultez « Mt.exe » sur le site Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**AssemblyIdentity**|Paramètre **String** facultatif.<br /><br /> Spécifie les valeurs d'attribut de l'élément **assemblyIdentity** du manifeste.  Spécifiez une liste délimitée par des virgules, où le premier composant est la valeur de l'attribut `name`, suivi par une ou plusieurs paires nom\/valeur au format, *\<attribute name\>\=\<attribute\_value\>*.<br /><br /> Pour plus d'informations, consultez l'option **\/identity** dans « Mt.exe » sur le site Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**ComponentFileName**|Paramètre **String** facultatif.<br /><br /> Spécifie le nom de la bibliothèque de liens dynamiques que vous souhaitez générer à partir des fichiers .rgs ou .tlb.  Ce paramètre est obligatoire si vous spécifiez les paramètres de tâche MT **RegistrarScriptFile** ou **TypeLibraryFile**.<br /><br /> Pour plus d'informations, consultez l'option **\/dll** dans « Mt.exe » sur le site Web  [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**DependencyInformationFile**|Paramètre **String** facultatif.<br /><br /> Spécifie le fichier d'informations sur les dépendances utilisé par Visual Studio pour effectuer le suivi des informations sur les dépendances de génération pour l'outil Manifeste.|  
|**EmbedManifest**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, incorpore le fichier manifeste dans l'assembly.  Si `false`, crée comme un fichier manifeste autonome.|  
|**EnableDPIAwareness**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, ajoute aux informations de manifeste qui marquent l'application comme compatible DPI.  L'écriture d'une application DPI rend une apparence d'interface utilisateur généralement correcte à travers une large gamme de paramètres d'affichage DPI élevé.<br /><br /> Pour plus d'informations, consultez « Résolutions élevées » sur le site Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**GenerateCatalogFiles**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, génère des fichiers de définition de catalogue \(.cdf\).<br /><br /> Pour plus d'informations, consultez l'option **\/makecdfs** dans « Mt.exe » sur le site Web  [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**GenerateCategoryTags**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, provoque la génération des  balises de catégorie.  Si ce paramètre est `true`, le paramètre de la tâche **ManifestFromManagedAssemblyMT** doit être également être spécifié.<br /><br /> Pour plus d'informations, consultez l'option **\/category** dans « Mt.exe » sur le site Web  [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**InputResourceManifests**|Paramètre **String** facultatif.<br /><br /> Entrez le manifeste d'une ressource de type RT\_MANIFEST qui a l'identificateur spécifié.  Spécifiez une ressource au format, *\<file\>\[***;***\[***\#***\]\<resource\_id\>\]*, où le paramètre facultatif `resource_id` est un nombre 16 bits non\-négatif.<br /><br /> Si aucun `resource_id` n'est spécifié, la valeur par défaut CREATEPROCESS\_MANIFEST\_RESOURCE \(1\) est utilisée.<br /><br /> Pour plus d'informations, consultez l'option **\/inputresource** dans « Mt.exe » sur le site Web  [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**ManifestFromManagedAssembly**|Paramètre **String** facultatif.<br /><br /> Génère un manifeste de l'assembly managé spécifié.<br /><br /> Pour plus d'informations, consultez l'option **\/managedassemblyname** dans « Mt.exe » sur le site Web  [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**ManifestToIgnore**|Paramètre **String** facultatif.<br /><br /> \(Non utilisé.\)|  
|**OutputManifestFile**|Paramètre **String** facultatif.<br /><br /> Spécifie le nom du manifeste de sortie.  Si ce paramètre est omis et un seul manifeste fonctionne, ce manifeste est modifié sur place.<br /><br /> Pour plus d'informations, consultez l'option **\/out** dans « Mt.exe » sur le site Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**OutputResourceManifests**|Paramètre **String** facultatif.<br /><br /> Envoie le manifeste vers une ressource de type RT\_MANIFEST qui est associée à l'identificateur spécifié.  Le format de la ressource est *\<file\>\[***;***\[***\#***\]\<resource\_id\>\]*, où le paramètre facultatif `resource_id` est un nombre 16 bits non\-négatif.<br /><br /> Si aucun `resource_id` n'est spécifié, la valeur par défaut CREATEPROCESS\_MANIFEST\_RESOURCE \(1\) est utilisée.<br /><br /> Pour plus d'informations, consultez l'option **\/outputresource** dans « Mt.exe » sur le site Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**RegistrarScriptFile**|Paramètre **String** facultatif.<br /><br /> Spécifie le nom du fichier de script d'inscription \(.rgs\) à utiliser pour la prise en charge du manifeste COM sans inscription.<br /><br /> Pour plus d'informations, consultez l'option **\/rgs** dans « Mt.exe » sur le site Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**ReplacementsFile**|Paramètre **String** facultatif.<br /><br /> Spécifie le fichier qui contient les valeurs des chaînes remplaçables dans le fichier de script d'inscription \(.rgs\).<br /><br /> Pour plus d'informations, consultez l'option **\/replacements** dans « Mt.exe » sur le site Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**ResourceOutputFileName**|Paramètre **String** facultatif.<br /><br /> Spécifie le fichier de ressources de sortie utilisés pour incorporer le manifeste dans la sortie de projet.|  
|**Sources**|Paramètre `ITaskItem[]` facultatif.<br /><br /> Spécifie une liste de fichiers sources de manifeste séparés par des espaces.<br /><br /> Pour plus d'informations, consultez l'option **\/manifest** dans « Mt.exe » sur le site Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**SuppressDependencyElement**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, génère un manifeste sans des éléments de dépendance.  Si ce paramètre est `true`, spécifiez également le paramètre de la tâche **ManifestFromManagedAssemblyMT**.<br /><br /> Pour plus d'informations, consultez l'option **\/nodependency** dans « Mt.exe » sur le site Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**SuppressStartupBanner**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, empêche l'affichage du copyright et du numéro de version lorsque la tâche démarre.<br /><br /> Pour plus d'informations, consultez l'option **\/nologo** dans « Mt.exe » sur le site Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**TrackerLogDirectory**|Paramètre `String` facultatif.<br /><br /> Spécifie le répertoire intermédiaire où les journaux de Tracker de cette tâche sont stockés.|  
|**TypeLibraryFile**|Paramètre **String** facultatif.<br /><br /> Spécifie le nom du fichier bibliothèque de types \(.tlb\).  Si vous spécifiez ce paramètre, spécifiez également le paramètre de la tâche **ComponentFileNameMT**.<br /><br /> Pour plus d'informations, consultez l'option **\/tlb** dans « Mt.exe » sur le site Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**UpdateFileHashes**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, calcule la valeur de hachage des fichiers au niveau du chemin d'accès spécifié par le paramètre de la tâche **UpdateFileHashesSearchPathMT**, puis met à jour la valeur de l'attribut **hash** de l'élément **file** du manifeste à l'aide de la valeur calculée.<br /><br /> Pour plus d'informations, consultez l'option **\/hashupdate** dans « Mt.exe » sur le site Web  [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  Consultez également le paramètre **UpdateFileHashesSearchPath** dans ce tableau.|  
|**UpdateFileHashesSearchPath**|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin de recherche à utiliser lorsque les fichiers à hacher sont mis à jour.  Utilisez ce paramètre avec le paramètre de tâche **UpdateFileHashesMT**.<br /><br /> Pour plus d'informations, consultez le paramètre **UpdateFileHashes** dans ce tableau.|  
|**VerboseOutput**|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, affiche les informations de débogage détaillées.<br /><br /> Pour plus d'informations, consultez l'option **\/verbose** dans « Mt.exe » sur le site Web  [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
  
## Notes  
  
## Voir aussi  
 [Task Reference](../msbuild/msbuild-task-reference.md)