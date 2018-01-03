---
title: "GenerateDeploymentManifest, tâche | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#GenerateDeploymentManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateDeploymentManifest task
- GenerateDeploymentManifest task [MSBuild]
ms.assetid: 0734ebda-734d-49c4-9642-8d9d919d45fd
caps.latest.revision: "27"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1dc0d1af8c79fe95ea091ac691519653b59a9648
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest, tâche
Génère un manifeste de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Un manifeste de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] décrit le déploiement d’une application en définissant une identité unique pour le déploiement, en identifiant des caractéristiques de déploiement comme le mode d’installation ou le mode en ligne, en spécifiant les paramètres de mise à jour de l’application et les emplacements de mise à jour, et en indiquant le manifeste d’application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] correspondant.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `GenerateDeploymentManifest`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AssemblyName`|Paramètre `String` facultatif.<br /><br /> Spécifie le champ `Name` de l’identité d’assembly pour le manifeste généré. Si vous ne spécifiez pas ce paramètre, le nom est déduit du paramètre `EntryPoint` ou `InputManifest`. Si le nom ne peut pas être déduit, la tâche génère une erreur.|  
|`AssemblyVersion`|Paramètre `String` facultatif.<br /><br /> Spécifie le champ `Version` de l’identité d’assembly pour le manifeste généré. Si vous ne spécifiez pas ce paramètre, la tâche utilise la valeur « 1.0.0.0 ».|  
|`CreateDesktopShortcut`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est true, une icône est créée sur le Bureau pendant l’installation d’application ClickOnce.|  
|`DeploymentUrl`|Paramètre `String` facultatif.<br /><br /> Spécifie l’emplacement de mise à jour de l’application. Si vous ne spécifiez pas ce paramètre, aucun emplacement de mise à jour n’est défini pour l’application. Toutefois, si le paramètre `UpdateEnabled` est `true`, vous devez spécifier l’emplacement de mise à jour. La valeur spécifiée doit être un chemin URL ou UNC complet.|  
|`Description`|Paramètre `String` facultatif.<br /><br /> Spécifie une description facultative pour l’application.|  
|`DisallowUrlActivation`|Paramètre `Boolean` facultatif.<br /><br /> Indique si l’application doit être exécutée automatiquement quand elle est ouverte par le biais d’une URL. Si ce paramètre est `true`, l’application peut être démarrée uniquement à partir du menu Démarrer. La valeur par défaut de ce paramètre est `false`. Cette entrée s’applique uniquement quand le paramètre `Install` a la valeur `true`.|  
|`EntryPoint`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Indique le point d’entrée de l’assembly de manifeste généré. Pour un manifeste de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], cette entrée spécifie le manifeste d’application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].<br /><br /> Dans [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)], la tâche [GenerateApplicationManifest](../msbuild/generateapplicationmanifest-task.md) nécessitait un `EntryPoint` pour générer un manifeste d’application. (Les manifestes d’assemblys ou natifs ne nécessitent pas de `EntryPoint`.) Cette exigence était appliquée avec l’erreur de build : « MSB3185: Paramètre EntryPoint non spécifié pour le manifeste. »<br /><br /> [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ne génère pas cette erreur quand le paramètre de la tâche `EntryPoint` n’est pas spécifié. Au lieu de cela, la balise \<customHostSpecified> est insérée comme enfant de la balise \<entryPoint>, par exemple :<br /><br /> `<entryPoint xmlns="urn:schemas-`<br /><br /> `microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> Vous pouvez ajouter des dépendances de DLL au manifeste d’application en effectuant les étapes suivantes :<br /><br /> 1.  Résolvez les références d’assembly avec un appel à <xref:Microsoft.Build.Tasks.ResolveAssemblyReference>.<br />2.  Passez la sortie de la tâche précédente et l’assembly lui-même à <xref:Microsoft.Build.Tasks.ResolveManifestFiles>.<br />3.  Passez les dépendances à l’aide du paramètre `Dependencies` à <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>.|  
|`ErrorReportUrl`|Paramètre <xref:System.String?displayProperty=fullName> facultatif.<br /><br /> Spécifie l’URL de la page web affichée dans les boîtes de dialogue pendant les installations ClickOnce.|  
|`InputManifest`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Indique un document XML d’entrée à utiliser comme base pour le générateur de manifeste. Ainsi, les données structurées telles que les définitions de manifeste personnalisées sont reflétées dans le manifeste de sortie. L’élément racine dans le document XML doit être un nœud d’assembly dans l’espace de noms asmv1.|  
|`Install`|Paramètre `Boolean` facultatif.<br /><br /> Indique si l’application est une application installée ou une application en ligne uniquement. Si ce paramètre est `true`, l’application est installée dans le menu Démarrer de l’utilisateur et peut être supprimée à l’aide de la boîte de dialogue Ajout/Suppression de programmes. Si ce paramètre est `false`, l’application est conçue pour une utilisation en ligne à partir d’une page web. La valeur par défaut de ce paramètre est `true`.|  
|`MapFileExtensions`|Paramètre `Boolean` facultatif.<br /><br /> Indique si le mappage d’extension de nom de fichier .deploy est utilisé. Si ce paramètre est `true`, chaque fichier programme est publié avec une extension de nom de fichier .deploy. Cette option est utile pour la sécurité de serveur web, afin de limiter le nombre d’extensions de nom de fichier qui doivent être débloquées pour activer le déploiement d’application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. La valeur par défaut de ce paramètre est `false`.|  
|`MaxTargetPath`|Paramètre `String` facultatif.<br /><br /> Spécifie la longueur maximale autorisée d’un chemin de fichier dans un déploiement d’application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Si vous spécifiez ce paramètre, la longueur de chaque chemin de fichier dans l’application est comparée à cette limite. Tout élément qui dépasse la limite provoque l’affichage d’un avertissement de génération. Si cette entrée n’est pas spécifiée ou est égale à zéro, aucune vérification n’est effectuée.|  
|`MinimumRequiredVersion`|Paramètre `String` facultatif.<br /><br /> Indique si l’utilisateur peut ignorer la mise à jour. Si l’utilisateur a une version antérieure à la version minimale requise, il ne pourra pas ignorer la mise à jour. Cette entrée s’applique uniquement quand le paramètre `Install` a la valeur `true`.|  
|`OutputManifest`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le nom du fichier manifeste de sortie généré. Si vous ne spécifiez pas ce paramètre, le nom du fichier de sortie est déduit de l’identité du manifeste généré.|  
|`Platform`|Paramètre `String` facultatif.<br /><br /> Spécifie la plateforme cible de l’application. Ce paramètre peut avoir les valeurs suivantes :<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> La valeur par défaut est `AnyCPU`.|  
|`Product`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom de l’application. Si vous ne spécifiez pas ce paramètre, le nom est déduit de l’identité du manifeste généré. Ce nom est utilisé comme nom du raccourci dans le menu Démarrer. Il fait partie du nom qui apparaît dans la boîte de dialogue Ajout/Suppression de programmes.|  
|`Publisher`|Paramètre `String` facultatif.<br /><br /> Spécifie l’éditeur de l’application. Si vous ne spécifiez pas ce paramètre, le nom est déduit de l’utilisateur enregistré ou de l’identité du manifeste généré. Ce nom est utilisé comme nom du dossier dans le menu Démarrer. Il fait partie du nom qui apparaît dans la boîte de dialogue Ajout/Suppression de programmes.|  
|`SuiteNamel`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom du dossier dans le menu Démarrer où figure l’application après le déploiement ClickOnce.|  
|`SupportUrl`|Paramètre `String` facultatif.<br /><br /> Spécifie le lien qui apparaît dans la boîte de dialogue Ajout/Suppression de programmes pour l’application. La valeur spécifiée doit être un chemin URL ou UNC complet.|  
|`TargetCulture`|Paramètre `String` facultatif.<br /><br /> Identifie la culture de l’application et spécifie le champ `Language` de l’identité d’assembly pour le manifeste généré. Si vous ne spécifiez pas ce paramètre, il est supposé que l’application est indifférente quant à la culture.|  
|`TrustUrlParameters`|Paramètre `Boolean` facultatif.<br /><br /> Indique si les paramètres de chaîne de requête URL doivent être accessibles à l’application. La valeur par défaut de ce paramètre est `false`, ce qui signifie que les paramètres ne seront pas accessibles à l’application.|  
|`UpdateEnabled`|Paramètre `Boolean` facultatif.<br /><br /> Indique si l’application est activée pour les mises à jour. La valeur par défaut de ce paramètre est `false`. Ce paramètre s’applique uniquement quand le paramètre `Install` a la valeur `true`.|  
|`UpdateInterval`|Paramètre `Int32` facultatif.<br /><br /> Spécifie l’intervalle de mise à jour de l’application. La valeur par défaut de ce paramètre est zéro. Ce paramètre s’applique uniquement quand les paramètres `Install` et `UpdateEnabled` ont tous deux la valeur `true`.|  
|`UpdateMode`|Paramètre `String` facultatif.<br /><br /> Indique si les mises à jour doivent être vérifiées au premier plan avant de démarrer l’application, ou en arrière-plan pendant l’exécution de l’application. Ce paramètre peut avoir les valeurs suivantes :<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> La valeur par défaut de ce paramètre est `Background`. Ce paramètre s’applique uniquement quand les paramètres `Install` et `UpdateEnabled` ont tous deux la valeur `true`.|  
|`UpdateUnit`|Paramètre `String` facultatif.<br /><br /> Spécifie les unités pour le paramètre `UpdateInterval`. Ce paramètre peut avoir les valeurs suivantes :<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Ce paramètre s’applique uniquement quand les paramètres `Install` et `UpdateEnabled` ont tous deux la valeur `true`.|  
  
## <a name="remarks"></a>Notes  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.GenerateManifestBase>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste des paramètres de la classe Task, consultez [Task, classe de base](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [GenerateApplicationManifest, tâche](../msbuild/generateapplicationmanifest-task.md)   
 [SignFile, tâche](../msbuild/signfile-task.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)