---
title: "Obtention de journaux de génération avec MSBuild | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
caps.latest.revision: "27"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 129f9c9235035e828e1825898aac89eaf8cd1388
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="obtaining-build-logs-with-msbuild"></a>Obtention de journaux de génération avec MSBuild
En utilisant des commutateurs avec MSBuild, vous pouvez indiquer le nombre de données de build que vous souhaitez vérifier, et spécifier si vous voulez enregistrer les données de build dans un ou plusieurs fichiers. Vous pouvez également spécifier un enregistreur d’événements personnalisé pour collecter les données de build. Pour plus d’informations sur les commutateurs de ligne de commande MSBuild que cette rubrique ne traite pas, consultez l’article [Command-Line Reference (Informations de référence sur la ligne de commande MSBuild)](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Si vous générez des projets à l’aide de l’IDE de Visual Studio, vous pouvez résoudre les problèmes de ces builds en passant en revue les journaux de génération. Pour plus d’informations, consultez l’article [Comment : afficher, enregistrer et configurer des fichiers journaux de génération](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
## <a name="setting-the-level-of-detail"></a>Définition du niveau de détail  
 Lorsque vous générez un projet à l’aide de MSBuild sans spécifier un niveau de détail, les informations suivantes apparaissent dans le journal de sortie :  
  
-   Erreurs, avertissements et messages qui sont classés comme très importants  
  
-   Certains événements d’état  
  
-   Résumé de la génération  
  
 En utilisant le commutateur **/verbosity** (**/v**), vous pouvez contrôler la quantité de données affichées dans le journal de sortie. Pour la résolution des problèmes, utilisez un niveau de détail `detailed` (`d`) ou `diagnostic` (`diag`), qui fournit le plus d’informations.  
  
 Le processus de génération peut être plus lent si vous définissez le commutateur **/verbosity** sur `detailed`, et même encore plus lent si vous définissez le commutateur **/verbosity** sur `diagnostic`.  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  
  
## <a name="saving-the-build-log-to-a-file"></a>Enregistrement du journal de la génération dans un fichier  
 Vous pouvez utiliser le commutateur **/fileLogger** (**fl**) pour enregistrer les données de build dans un fichier. Dans l’exemple suivant, les données de build sont enregistrées dans un fichier nommé `msbuild.log`.  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 Dans l’exemple suivant, le fichier journal est nommé `MyProjectOutput.log`, et le niveau de détail de sa sortie est défini sur `diagnostic`. Le commutateur **/filelogparameters** (`flp`) vous permet de spécifier ces deux paramètres.  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 Pour plus d’informations, consultez [Informations de référence sur la ligne de commande](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="saving-the-log-output-to-multiple-files"></a>Enregistrement du journal de sortie dans plusieurs fichiers  
 Dans l’exemple suivant, la totalité du journal est enregistrée dans `msbuild1.log`, les erreurs le sont dans `JustErrors.log`, et les avertissements dans `JustWarnings.log`. Cet exemple utilise des numéros de fichier pour chacun des trois fichiers. Les numéros de fichier sont spécifiés juste après les commutateurs **/fl** et **/flp** (par exemple, `/fl1` et `/flp1`).  
  
 Les commutateurs **/filelogparameters** (`flp`) des fichiers 2 et 3 indiquent comment nommer chaque fichier et les éléments à y inclure. Comme aucun nom n’est spécifié pour le fichier 1, le nom par défaut `msbuild1.log` est utilisé.  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 Pour plus d’informations, consultez [Informations de référence sur la ligne de commande](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="using-a-custom-logger"></a>Utilisation d'un journal personnalisé  
 Vous pouvez écrire votre propre enregistreur d’événements en créant un type managé qui implémente l’interface <xref:Microsoft.Build.Framework.ILogger>. Vous pouvez utiliser un enregistreur d’événements personnalisé, par exemple, pour envoyer des erreurs de build par courrier électronique, et les enregistrer dans une base de données ou dans un fichier XML. Pour plus d’informations, consultez l’article [Enregistreurs d’événements de génération](../msbuild/build-loggers.md).  
  
 Dans la ligne de commande MSBuild, vous spécifiez l’enregistreur d’événements personnalisé à l’aide du commutateur **Logger**. Vous pouvez également utiliser le commutateur **/noconsolelogger** pour désactiver l’enregistreur d’événements de console par défaut.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Enregistreurs d’événements de génération](../msbuild/build-loggers.md)   
 [Journalisation dans un environnement multiprocesseur](../msbuild/logging-in-a-multi-processor-environment.md)   
 [Création d’enregistreurs d’événements de transfert](../msbuild/creating-forwarding-loggers.md)   
 [Concepts MSBuild](../msbuild/msbuild-concepts.md)