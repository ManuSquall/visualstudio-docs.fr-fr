---
title: Obtention de journaux de génération avec MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 37c2c9b1ff1380fc8a8f4a96f64a45a0a7fbd1b6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53925860"
---
# <a name="obtain-build-logs-with-msbuild"></a>Obtenir des journaux de génération avec MSBuild

En utilisant des commutateurs avec MSBuild, vous pouvez indiquer le nombre de données de build que vous souhaitez vérifier, et spécifier si vous voulez enregistrer les données de build dans un ou plusieurs fichiers. Vous pouvez également spécifier un enregistreur d’événements personnalisé pour collecter les données de build. Pour plus d’informations sur les commutateurs de ligne de commande MSBuild que cette rubrique ne traite pas, consultez l’article [Command-Line Reference (Informations de référence sur la ligne de commande MSBuild)](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
> Si vous générez des projets à l’aide de l’IDE de Visual Studio, vous pouvez résoudre les problèmes de ces builds en passant en revue les journaux de génération. Pour plus d'informations, voir [Procédure : afficher, enregistrer et configurer des fichiers journaux de génération](../ide/how-to-view-save-and-configure-build-log-files.md).
  
## <a name="set-the-level-of-detail"></a>Définir le niveau de détail  

 Lorsque vous générez un projet à l’aide de MSBuild sans spécifier un niveau de détail, les informations suivantes apparaissent dans le journal de sortie :  
  
- Erreurs, avertissements et messages qui sont classés comme très importants  
  
- Certains événements d’état  
  
- Résumé de la génération  

En utilisant le commutateur **-verbosity** (**-v**), vous pouvez contrôler le volume de données affichées dans le journal de sortie. Pour la résolution des problèmes, utilisez un niveau de détail `detailed` (`d`) ou `diagnostic` (`diag`), qui fournit le plus d’informations.  

Le processus de build peut être plus lent si le commutateur **-verbosity** est défini sur `detailed`, et encore plus si le commutateur **-verbosity** est défini sur `diagnostic`.  

```cmd
msbuild MyProject.proj -t:go -v:diag  
```  

### <a name="verbosity-settings"></a>Paramètres du niveau de détail

Le tableau suivant montre comment le niveau de détail du journal (valeurs de colonne) affecte les types de messages (valeurs de ligne) qui sont enregistrés.

|                                       | Quiet | Minimal | Normale | Détaillé | Diagnostic |
|---------------------------------------|:-----:|:-------:|:------:|:--------:|:----------:|
| Erreurs                                |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Avertissements                              |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Messages avec une importance haute              |       |    ✅    |    ✅   |     ✅    |      ✅     |
| Messages avec une importance normale           |       |         |    ✅   |     ✅    |      ✅     |
| Messages avec une importance faible              |       |         |        |     ✅    |      ✅     |
| Informations supplémentaires du moteur MSBuild |       |         |        |          |      ✅     |

## <a name="save-the-build-log-to-a-file"></a>Enregistrer le journal de génération dans un fichier  

Vous pouvez utiliser le commutateur **-fileLogger** (**fl**) pour enregistrer les données de build dans un fichier. Dans l’exemple suivant, les données de build sont enregistrées dans un fichier nommé *msbuild.log*.  

```cmd  
msbuild MyProject.proj -t:go -fileLogger  
```  

 Dans l’exemple suivant, le fichier journal est nommé *MyProjectOutput.log*, et le niveau de détail de sa sortie est défini sur `diagnostic`. Le commutateur **-filelogparameters** (`flp`) permet de spécifier ces deux paramètres.  

```cmd  
msbuild MyProject.proj -t:go -fl -flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  

 Pour plus d’informations, consultez [Référence de ligne de commande](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="save-the-log-output-to-multiple-files"></a>Enregistrer le journal de sortie dans plusieurs fichiers  

 Dans l’exemple suivant, la totalité du journal est enregistrée dans *msbuild1.log*, les erreurs le sont dans *JustErrors.log* et les avertissements dans *JustWarnings.log*. Cet exemple utilise des numéros de fichier pour chacun des trois fichiers. Les numéros de fichier sont spécifiés juste après les commutateurs **-fl** et **-flp** (par exemple, `-fl1` et `-flp1`).  
  
 Les commutateurs **-filelogparameters** (`flp`) des fichiers 2 et 3 indiquent comment nommer chaque fichier et quels éléments y inclure. Comme aucun nom n’est spécifié pour le fichier 1, le nom par défaut *msbuild1.log* est utilisé.  

```cmd  
msbuild MyProject.proj -t:go -fl1 -fl2 -fl3 -flp2:logfile=JustErrors.log;errorsonly -flp3:logfile=JustWarnings.log;warningsonly  
```  

 Pour plus d’informations, consultez [Référence de ligne de commande](../msbuild/msbuild-command-line-reference.md).  

## <a name="save-a-binary-log"></a>Enregistrer un journal binaire

Vous pouvez enregistrer le journal dans un format binaire compressé à l’aide du commutateur **-binaryLogger** (**bl**). Ce journal inclut une description détaillée du processus de génération et peut être lu par certains outils d’analyse de journaux.

Dans l’exemple suivant, un fichier journal binaire est créé avec le nom *binarylogfilename*.

```cmd  
/bl:binarylogfilename.binlog
``` 

Pour plus d’informations, consultez [Référence de ligne de commande](../msbuild/msbuild-command-line-reference.md).  

## <a name="use-a-custom-logger"></a>Utiliser un journal personnalisé  

 Vous pouvez écrire votre propre enregistreur d’événements en créant un type managé qui implémente l’interface <xref:Microsoft.Build.Framework.ILogger>. Vous pouvez utiliser un enregistreur d’événements personnalisé, par exemple, pour envoyer des erreurs de build par courrier électronique, et les enregistrer dans une base de données ou dans un fichier XML. Pour plus d’informations, consultez l’article [Enregistreurs d’événements de génération](../msbuild/build-loggers.md).  
  
 Dans la ligne de commande MSBuild, vous pouvez spécifier l’enregistreur d’événements personnalisé à l’aide du commutateur **-logger**. Par ailleurs, le commutateur **-noconsolelogger** permet de désactiver l’enregistreur d’événements de console par défaut.  
  
## <a name="see-also"></a>Voir aussi  

 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Enregistreurs d’événements de génération](../msbuild/build-loggers.md)   
 [Journalisation dans un environnement multiprocesseur](../msbuild/logging-in-a-multi-processor-environment.md)   
 [Création d’enregistreurs d’événements de transfert](../msbuild/creating-forwarding-loggers.md)   
 [Concepts MSBuild](../msbuild/msbuild-concepts.md)