---
title: "Obtention de journaux de g&#233;n&#233;ration avec MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, journalisation"
  - "journalisation [MSBuild]"
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Obtention de journaux de g&#233;n&#233;ration avec MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

À l'aide de les commutateurs avec MSBuild, vous pouvez spécifier le nombre de données de génération vous souhaitez examiner et si vous souhaitez enregistrer des données de génération à un ou plusieurs fichiers.  Vous pouvez également spécifier un journal personnalisé pour collecter des données de génération.  Pour plus d'informations sur les commutateurs de ligne de commande MSBuild que cette rubrique ne traite pas, consultez [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Si vous générez des projets à l'aide de l'IDE de Visual Studio, vous pouvez résoudre ces builds en examinant les journaux de génération.  Pour plus d'informations, consultez [Comment : afficher, enregistrer et configurer des fichiers journaux de génération](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
## Définition du niveau de détail  
 Lorsque vous générez un projet à l'aide de MSBuild sans spécifier un niveau de détail, les informations suivantes s'affichent dans le journal de sortie :  
  
-   Erreurs, avertissements, et messages qui sont catégorisés comme très importants.  
  
-   Certains événements d'état.  
  
-   Un résumé de la build.  
  
 À l'aide de le commutateur d' **\/verbosity** \(**\/v**\), vous pouvez contrôler la quantité de données apparaissent dans le journal de sortie.  Pour déboguer, utilisez un niveau de détail d' `detailed` \(`d`\) ou d' `diagnostic` \(`diag`\), qui fournit la plupart d'informations.  
  
 Le processus de génération peut être plus lente lorsque vous **\/verbosity** défini à `detailed` et encore plus lent lorsque vous définissez **\/verbosity** à `diagnostic`.  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  
  
## Enregistrer le journal de génération dans un fichier  
 Vous pouvez utiliser le commutateur d' **\/fileLogger** \(**fl**\) pour enregistrer des données de génération dans un fichier.  L'exemple suivant stocke les données de génération dans un fichier nommé `msbuild.log`.  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 Dans l'exemple suivant, le fichier journal est nommé `MyProjectOutput.log`, et les commentaires de la sortie de journal sont définies à `diagnostic`.  Vous spécifiez ces deux paramètres à l'aide de le commutateur d' **\/filelogparameters** \(`flp`\).  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 Pour plus d'informations, consultez [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md).  
  
## Stockant le journal de sortie en plusieurs fichiers  
 L'exemple suivant enregistre le journal entier à `msbuild1.log`, comme les erreurs à `JustErrors.log`, et uniquement les avertissements à `JustWarnings.log`.  L'exemple utilise des nombres de fichier pour les trois fichiers.  Les nombres de fichier sont spécifiés après les commutateurs de **\/fl** et d' **\/flp** \(par exemple, `/fl1` et `/flp1`\).  
  
 Les commutateurs de **\/filelogparameters** \(`flp`\) pour les fichiers 2 et 3 spécifient les éléments à nommer chaque fichier et les éléments à inclure dans chaque fichier.  Aucun nom n'est spécifié pour le fichier 1 ; le nom par défaut d' `msbuild1.log` est utilisé.  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 Pour plus d'informations, consultez [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md).  
  
## À l'aide d'un journal personnalisé  
 Vous pouvez écrire votre propre journal en créant un type managé qui implémente l'interface <xref:Microsoft.Build.Framework.ILogger>.  Vous pouvez utiliser un journal personnalisé, par exemple, pour envoyer des erreurs de build dans la messagerie électronique, les stocker dans une base de données, ou les stocker dans un fichier XML.  Pour plus d'informations, consultez [Build Loggers](../msbuild/build-loggers.md).  
  
 Dans la ligne de commande MSBuild, vous spécifiez le journal personnalisé à l'aide de le commutateur d' **\/logger** .  Vous pouvez également utiliser le commutateur d' **\/noconsolelogger** pour désactiver le journal de console par défaut.  
  
## Voir aussi  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Build Loggers](../msbuild/build-loggers.md)   
 [Logging in a Multi\-Processor Environment](../msbuild/logging-in-a-multi-processor-environment.md)   
 [Creating Forwarding Loggers](../msbuild/creating-forwarding-loggers.md)   
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)