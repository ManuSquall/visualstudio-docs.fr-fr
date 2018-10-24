---
title: Classe de base ToolTaskExtension | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- MSBuild.ToolTask.ToolCommandFailed
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 258ae433-f68a-49f1-b276-da20e3472e68
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8856011e8b85f049c53947a785f1479e1db25368
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888552"
---
# <a name="tooltaskextension-base-class"></a>Classe de base ToolTaskExtension
De nombreuses tâches héritent de la classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, laquelle hérite de la classe <xref:Microsoft.Build.Utilities.ToolTask>, qui hérite elle-même de la classe <xref:Microsoft.Build.Utilities.Task>. Cette chaîne d'héritage ajoute plusieurs paramètres aux tâches qui en dérivent. Ces paramètres sont répertoriés dans ce document.  

## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres des classes de base.  


| Paramètre | Description |
| - | - |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine%2A> | Paramètre <xref:Microsoft.Build.Framework.IBuildEngine> facultatif.<br /><br /> Spécifie l'interface du moteur de génération disponible pour les tâches. Le moteur de génération définit automatiquement ce paramètre pour permettre aux tâches d’être rappelées. |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A> | Paramètre <xref:Microsoft.Build.Framework.IBuildEngine2> facultatif.<br /><br /> Spécifie l'interface du moteur de génération disponible pour les tâches. Le moteur de génération définit automatiquement ce paramètre pour permettre aux tâches d’être rappelées.<br /><br /> Il s’agit d’une propriété de convenance qui permet aux auteurs de tâches qui héritent de cette classe de ne pas avoir à effectuer un cast de la valeur de `IBuildEngine` vers `IBuildEngine2`. |
| <xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A> | Paramètre <xref:Microsoft.Build.Framework.IBuildEngine3> facultatif.<br /><br /> Spécifie l'interface du moteur de génération fournie par l'hôte. |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | Paramètre `bool` facultatif.<br /><br /> Quand la valeur est `true`, cette tâche passe **/Q** à la ligne de commande *cmd.exe* de telle manière que cette dernière ne soit pas copiée dans stdout. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | Paramètres de tableau `String` facultatif.<br /><br /> Tableau de paires de variables d'environnement, séparées par un signe égal. Ces variables sont transmises à l'exécutable généré en plus ou en remplacement sélectif du bloc environnement normal. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | Paramètre en lecture seule de sortie `Int32` facultatif.<br /><br /> Spécifie le code de sortie fourni par la commande exécutée. Si la tâche a journalisé des erreurs, alors que le processus avait un code de sortie de 0 (réussite), ce paramètre prend la valeur -1. |
| <xref:Microsoft.Build.Utilities.Task.HostObject%2A> | Paramètre <xref:Microsoft.Build.Framework.ITaskHost> facultatif.<br /><br /> Spécifie l'instance de l'objet hôte (peut être null). Le moteur de génération définit cette propriété si l’IDE hôte a associé un objet hôte à cette tâche particulière. |
| <xref:Microsoft.Build.Tasks.ToolTaskExtension.Log%2A> | Paramètre en lecture seule <xref:Microsoft.Build.Utilities.TaskLoggingHelper> facultatif.<br /><br /> Obtient une instance d’une classe <xref:Microsoft.Build.Tasks.TaskLoggingHelperExtension> qui contient des méthodes de journalisation des tâches. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Paramètre `bool` d'option.<br /><br /> Si la valeur est `true`, tous les messages reçus sur le flux d'erreur standard sont journalisés en tant qu'erreurs. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | Paramètre `String` facultatif.<br /><br /> Importance avec laquelle le texte doit être enregistré dans le flux de sortie standard. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | Paramètre `String` facultatif.<br /><br /> Importance avec laquelle le texte doit être enregistré dans le flux de sortie standard. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Paramètre `Int32` facultatif virtuel.<br /><br /> Spécifie le délai, en millisecondes, après lequel l’exécutable de la tâche est arrêté. La valeur par défaut est `Int.MaxValue`, ce qui indique qu’il n’existe aucun délai d’expiration. Délai d’expiration en millisecondes. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Paramètre `string` facultatif virtuel.<br /><br /> Les projets peuvent l'implémenter pour remplacer un ToolName. Les tâches peuvent le remplacer pour préserver le ToolName. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | Paramètre `string` facultatif.<br /><br /> Spécifie l'emplacement à partir duquel la tâche charge le fichier exécutable sous-jacent. Si ce paramètre n’est pas spécifié, la tâche utilise le chemin d’installation du Kit de développement logiciel (SDK) qui correspond à la version de l’infrastructure qui exécute [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | Paramètre `bool` facultatif.<br /><br /> Quand la valeur est `true`, cette tâche crée un fichier de commandes pour la ligne de commande et l’exécute à l’aide de l’interpréteur de commandes au lieu d’exécuter la commande directement. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | Paramètre `bool` facultatif.<br /><br /> Quand la valeur est `true`, cette tâche donne le nœud quand sa tâche s’exécute. |

## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)   
 [Tâches](../msbuild/msbuild-tasks.md)