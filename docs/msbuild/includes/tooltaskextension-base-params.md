---
author: ghogen
ms.author: ghogen
ms.topic: include
ms.date: 4/23/2020
ms.openlocfilehash: 40108f56ee9d64688fc665fdef0e0ab731bddfff
ms.sourcegitcommit: 596f92fcc84e6f4494178863a66aed85afe0bb08
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82204425"
---
### <a name="tooltaskextension-parameters"></a>Paramètres ToolTaskExtension

Cette tâche hérite de la <xref:Microsoft.Build.Tasks.ToolTaskExtension> classe, qui hérite de la <xref:Microsoft.Build.Utilities.ToolTask> classe, qui elle-même hérite <xref:Microsoft.Build.Utilities.Task> de la classe. Cette chaîne d'héritage ajoute plusieurs paramètres aux tâches qui en dérivent.

Le tableau suivant décrit les paramètres des classes de base :

| Paramètre | Description |
| - | - |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | Paramètre `bool` facultatif.<br /><br /> Lorsque la valeur `true`est, cette tâche passe **/q** à la ligne de commande *cmd. exe* de sorte que la ligne de commande ne soit pas copiée dans stdout. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | Paramètres de tableau `String` facultatif.<br /><br /> Tableau de paires de variables d'environnement, séparées par un signe égal. Ces variables sont transmises à l'exécutable généré en plus ou en remplacement sélectif du bloc environnement normal. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | Paramètre en lecture seule de sortie `Int32` facultatif.<br /><br /> Spécifie le code de sortie fourni par la commande exécutée. Si la tâche a journalisé des erreurs, alors que le processus avait un code de sortie de 0 (réussite), ce paramètre prend la valeur -1. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Paramètre `bool` d'option.<br /><br /> Si la valeur est `true`, tous les messages reçus sur le flux d'erreur standard sont journalisés en tant qu'erreurs. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Paramètre `bool` facultatif.<br /><br /> Si la valeur est `true`, tous les messages reçus sur le flux d'erreur standard sont journalisés en tant qu'erreurs. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | Paramètre `String` facultatif.<br /><br /> Importance avec laquelle le texte doit être enregistré dans le flux de sortie standard. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | Paramètre `String` facultatif.<br /><br /> Importance avec laquelle le texte doit être enregistré dans le flux de sortie standard. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Paramètre `Int32` facultatif.<br /><br /> Spécifie le délai, en millisecondes, après lequel l’exécutable de la tâche est arrêté. La valeur par défaut est `Int.MaxValue`, ce qui indique qu’il n’existe aucun délai d’expiration. Délai d’expiration en millisecondes. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Paramètre `string` facultatif.<br /><br /> Les projets peuvent l'implémenter pour remplacer un ToolName. Les tâches peuvent le remplacer pour préserver le ToolName. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | Paramètre `string` facultatif.<br /><br /> Spécifie l’emplacement à partir duquel la tâche charge le fichier exécutable sous-jacent. Si ce paramètre n’est pas spécifié, la tâche utilise le chemin d’installation du kit de développement logiciel (SDK) qui correspond à la version du Framework qui exécute MSBuild. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | Paramètre `bool` facultatif.<br /><br /> Quand la valeur est `true`, cette tâche crée un fichier de commandes pour la ligne de commande et l'exécute à l'aide de l'interpréteur de commandes au lieu d'exécuter la commande directement. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | Paramètre `bool` facultatif.<br /><br /> Quand la valeur est `true`, cette tâche donne le nœud quand sa tâche s'exécute. |
