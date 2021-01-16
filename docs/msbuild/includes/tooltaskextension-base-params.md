---
author: ghogen
ms.author: ghogen
ms.topic: include
ms.date: 4/23/2020
ms.openlocfilehash: d7d4027c53f599b4a17d267d5ebf72eee1ed296b
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2021
ms.locfileid: "98535302"
---
### <a name="tooltaskextension-parameters"></a>Paramètres ToolTaskExtension

Cette tâche hérite de la <xref:Microsoft.Build.Tasks.ToolTaskExtension> classe, qui hérite de la <xref:Microsoft.Build.Utilities.ToolTask> classe, qui elle-même hérite de la <xref:Microsoft.Build.Utilities.Task> classe. Cette chaîne d'héritage ajoute plusieurs paramètres aux tâches qui en dérivent.

Le tableau suivant décrit les paramètres des classes de base :

| Paramètre | Description |
| - | - |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | Paramètre `bool` facultatif.<br /><br /> Lorsque la valeur `true` est, cette tâche passe **/q** à la ligne de commande *cmd.exe* , de telle sorte que la ligne de commande ne soit pas copiée dans stdout. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | Paramètres de tableau `String` facultatif.<br /><br /> Tableau de définitions de variables d’environnement, séparées par des points-virgules. Chaque définition doit spécifier un nom et une valeur de variable d’environnement séparés par un signe égal. Ces variables sont transmises à l'exécutable généré en plus ou en remplacement sélectif du bloc environnement normal. Par exemple, `Variable1=Value1;Variable2=Value2`. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | Paramètre en lecture seule de sortie `Int32` facultatif.<br /><br /> Spécifie le code de sortie fourni par la commande exécutée. Si la tâche a journalisé des erreurs, alors que le processus avait un code de sortie de 0 (réussite), ce paramètre prend la valeur -1. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Paramètre `bool` facultatif.<br /><br /> Si la valeur est `true`, tous les messages reçus sur le flux d'erreur standard sont journalisés en tant qu'erreurs. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | Paramètre `String` facultatif.<br /><br /> Importance avec laquelle le texte doit être enregistré dans le flux de sortie standard. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | Paramètre `String` facultatif.<br /><br /> Importance avec laquelle le texte doit être enregistré dans le flux de sortie standard. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Paramètre `Int32` facultatif.<br /><br /> Spécifie le délai, en millisecondes, après lequel l’exécutable de la tâche est arrêté. La valeur par défaut est `Int.MaxValue`, ce qui indique qu’il n’existe aucun délai d’expiration. Délai d’expiration en millisecondes. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Paramètre `string` facultatif.<br /><br /> Les projets peuvent l'implémenter pour remplacer un ToolName. Les tâches peuvent le remplacer pour préserver le ToolName. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | Paramètre `string` facultatif.<br /><br /> Spécifie l’emplacement à partir duquel la tâche charge le fichier exécutable sous-jacent. Si ce paramètre n’est pas spécifié, la tâche utilise le chemin d’installation du kit de développement logiciel (SDK) qui correspond à la version du Framework qui exécute MSBuild. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | Paramètre `bool` facultatif.<br /><br /> Quand la valeur est `true`, cette tâche crée un fichier de commandes pour la ligne de commande et l'exécute à l'aide de l'interpréteur de commandes au lieu d'exécuter la commande directement. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | Paramètre `bool` facultatif.<br /><br /> Quand la valeur est `true`, cette tâche donne le nœud quand sa tâche s'exécute. |
