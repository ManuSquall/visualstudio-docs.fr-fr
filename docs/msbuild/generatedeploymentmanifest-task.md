---
title: GenerateDeploymentManifest, tâche | Microsoft Docs
description: Apprenez à utiliser la tâche MSBuild GenerateDeploymentManifest pour générer un manifeste de déploiement ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateDeploymentManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateDeploymentManifest task
- GenerateDeploymentManifest task [MSBuild]
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 436aeb1b318aaa98d8a8cc9d8dac6baf4dd3c6c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914767"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest (tâche)

Génère un manifeste de déploiement ClickOnce. Un manifeste de déploiement ClickOnce décrit le déploiement d’une application en définissant une identité unique pour le déploiement, en identifiant les caractéristiques de déploiement telles que l’installation ou le mode en ligne, en spécifiant les paramètres de mise à jour des applications et les emplacements des mises à jour, et en indiquant le manifeste d’application ClickOnce correspondant.

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la tâche `GenerateDeploymentManifest`.

| Paramètre | Description |
|--------------------------| - |
| `AssemblyName` | Paramètre `String` facultatif.<br /><br /> Spécifie le champ `Name` de l’identité d’assembly pour le manifeste généré. Si vous ne spécifiez pas ce paramètre, le nom est déduit du paramètre `EntryPoint` ou `InputManifest`. Si le nom ne peut pas être déduit, la tâche génère une erreur. |
| `AssemblyVersion` | Paramètre `String` facultatif.<br /><br /> Spécifie le champ `Version` de l’identité d’assembly pour le manifeste généré. Si vous ne spécifiez pas ce paramètre, la tâche utilise la valeur « 1.0.0.0 ». |
| `CreateDesktopShortcut` | Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est true, une icône est créée sur le Bureau pendant l’installation d’application ClickOnce. |
| `DeploymentUrl` | Paramètre `String` facultatif.<br /><br /> Spécifie l’emplacement de mise à jour de l’application. Si vous ne spécifiez pas ce paramètre, aucun emplacement de mise à jour n’est défini pour l’application. Toutefois, si le paramètre `UpdateEnabled` est `true`, vous devez spécifier l’emplacement de mise à jour. La valeur spécifiée doit être un chemin URL ou UNC complet. |
| `Description` | Paramètre `String` facultatif.<br /><br /> Spécifie une description facultative pour l’application. |
| `DisallowUrlActivation` | Paramètre `Boolean` facultatif.<br /><br /> Indique si l’application doit être exécutée automatiquement quand elle est ouverte par le biais d’une URL. Si ce paramètre a `true` la la, l’application peut être démarrée uniquement à partir du menu **Démarrer** . La valeur par défaut de ce paramètre est `false`. Cette entrée s’applique uniquement quand le paramètre `Install` a la valeur `true`. |
| `EntryPoint` | Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Indique le point d’entrée de l’assembly de manifeste généré. Pour un manifeste de déploiement ClickOnce, cette entrée spécifie le manifeste d’application ClickOnce.<br /><br />Si le paramètre de tâche `EntryPoint` n’est pas spécifié, la balise `<customHostSpecified>` est insérée en tant qu’enfant de la balise `<entryPoint>`, par exemple :<br /><br /> `<entryPoint xmlns="urn:schemas-microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> Vous pouvez ajouter des dépendances de DLL au manifeste d’application en effectuant les étapes suivantes :<br /><br /> 1. résolvez les références d’assembly avec un appel à <xref:Microsoft.Build.Tasks.ResolveAssemblyReference> .<br />2. passer la sortie de la tâche précédente et l’assembly lui-même à <xref:Microsoft.Build.Tasks.ResolveManifestFiles> .<br />3. passer les dépendances à l’aide du `Dependencies` paramètre à <xref:Microsoft.Build.Tasks.GenerateApplicationManifest> . |
| `ErrorReportUrl` | Paramètre <xref:System.String?displayProperty=fullName> facultatif.<br /><br /> Spécifie l’URL de la page web affichée dans les boîtes de dialogue pendant les installations ClickOnce. |
| `InputManifest` | Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Indique un document XML d’entrée à utiliser comme base pour le générateur de manifeste. Ainsi, les données structurées telles que les définitions de manifeste personnalisées sont reflétées dans le manifeste de sortie. L’élément racine dans le document XML doit être un nœud d’assembly dans l’espace de noms asmv1. |
| `Install` | Paramètre `Boolean` facultatif.<br /><br /> Indique si l’application est une application installée ou une application en ligne uniquement. Si ce paramètre est `true` , l’application est installée dans le menu **Démarrer** de l’utilisateur et peut être supprimée à l’aide de la boîte de dialogue **Ajout/suppression de programmes** . Si ce paramètre a la valeur `false`, l’application est conçue pour une utilisation en ligne à partir d’une page web. La valeur par défaut de ce paramètre est `true`. |
| `MapFileExtensions` | Paramètre `Boolean` facultatif.<br /><br /> Spécifie si le mappage d’extension de nom de fichier *. deploy* est utilisé. Si ce paramètre est `true` , chaque fichier programme est publié avec une extension de nom de fichier *. deploy* . Cette option est utile pour la sécurité du serveur Web afin de limiter le nombre d’extensions de nom de fichier qui doivent être débloquées pour activer le déploiement d’applications ClickOnce. La valeur par défaut de ce paramètre est `false`. |
| `MaxTargetPath` | Paramètre `String` facultatif.<br /><br /> Spécifie la longueur maximale autorisée d’un chemin d’accès de fichier dans un déploiement d’application ClickOnce. Si vous spécifiez ce paramètre, la longueur de chaque chemin de fichier dans l’application est comparée à cette limite. Tout élément qui dépasse la limite provoque l’affichage d’un avertissement de génération. Si cette entrée n’est pas spécifiée ou est égale à zéro, aucune vérification n’est effectuée. |
| `MinimumRequiredVersion` | Paramètre `String` facultatif.<br /><br /> Indique si l’utilisateur peut ignorer la mise à jour. Si l’utilisateur a une version antérieure à la version minimale requise, il ne pourra pas ignorer la mise à jour. Cette entrée s’applique uniquement quand le paramètre `Install` a la valeur `true`. |
| `OutputManifest` | Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le nom du fichier manifeste de sortie généré. Si vous ne spécifiez pas ce paramètre, le nom du fichier de sortie est déduit de l’identité du manifeste généré. |
| `Platform` | Paramètre `String` facultatif.<br /><br /> Spécifie la plateforme cible de l’application. Ce paramètre peut avoir les valeurs suivantes :<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> La valeur par défaut est `AnyCPU`. |
| `Product` | Paramètre `String` facultatif.<br /><br /> Spécifie le nom de l'application. Si vous ne spécifiez pas ce paramètre, le nom est déduit de l’identité du manifeste généré. Ce nom est utilisé pour le nom du raccourci dans le menu **Démarrer** et fait partie du nom qui apparaît dans la boîte de dialogue **Ajout/suppression de programmes** . |
| `Publisher` | Paramètre `String` facultatif.<br /><br /> Spécifie l’éditeur de l’application. Si vous ne spécifiez pas ce paramètre, le nom est déduit de l’utilisateur enregistré ou de l’identité du manifeste généré. Ce nom est utilisé pour le nom du dossier dans le menu **Démarrer** et fait partie du nom qui apparaît dans la boîte de dialogue **Ajout/suppression de programmes** . |
| `SuiteNamel` | Paramètre `String` facultatif.<br /><br /> Spécifie le nom du dossier dans le menu **Démarrer** dans lequel l’application se trouve après le déploiement ClickOnce. |
| `SupportUrl` | Paramètre `String` facultatif.<br /><br /> Spécifie le lien qui apparaît dans la boîte de dialogue **Ajout/suppression de programmes** pour l’application. La valeur spécifiée doit être un chemin URL ou UNC complet. |
| `TargetCulture` | Paramètre `String` facultatif.<br /><br /> Identifie la culture de l’application et spécifie le champ `Language` de l’identité d’assembly pour le manifeste généré. Si vous ne spécifiez pas ce paramètre, il est supposé que l’application est indifférente quant à la culture. |
| `TrustUrlParameters` | Paramètre `Boolean` facultatif.<br /><br /> Indique si les paramètres de chaîne de requête URL doivent être accessibles à l’application. La valeur par défaut de ce paramètre est `false`, ce qui signifie que les paramètres ne seront pas accessibles à l’application. |
| `UpdateEnabled` | Paramètre `Boolean` facultatif.<br /><br /> Indique si l’application est activée pour les mises à jour. La valeur par défaut de ce paramètre est `false`. Ce paramètre s’applique uniquement quand le paramètre `Install` a la valeur `true`. |
| `UpdateInterval` | Paramètre `Int32` facultatif.<br /><br /> Spécifie l’intervalle de mise à jour de l’application. La valeur par défaut de ce paramètre est zéro. Ce paramètre s’applique uniquement quand les paramètres `Install` et `UpdateEnabled` ont tous deux la valeur `true`. |
| `UpdateMode` | Paramètre `String` facultatif.<br /><br /> Indique si les mises à jour doivent être vérifiées au premier plan avant de démarrer l’application, ou en arrière-plan pendant l’exécution de l’application. Ce paramètre peut avoir les valeurs suivantes :<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> La valeur par défaut de ce paramètre est `Background`. Ce paramètre s’applique uniquement quand les paramètres `Install` et `UpdateEnabled` ont tous deux la valeur `true`. |
| `UpdateUnit` | Paramètre `String` facultatif.<br /><br /> Spécifie les unités pour le paramètre `UpdateInterval`. Ce paramètre peut avoir les valeurs suivantes :<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Ce paramètre s’applique uniquement quand les paramètres `Install` et `UpdateEnabled` ont tous deux la valeur `true`. |

## <a name="remarks"></a>Notes

En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.GenerateManifestBase> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour obtenir la liste des paramètres de la classe Task, consultez [Classe de base de tâche](../msbuild/task-base-class.md).

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [GenerateApplicationManifest (tâche)](../msbuild/generateapplicationmanifest-task.md)
- [SignFile (tâche)](../msbuild/signfile-task.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
