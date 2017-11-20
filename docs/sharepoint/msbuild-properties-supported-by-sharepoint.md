---
title: "Propriétés MSBuild prises en charge par SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, MSBuild properties
ms.assetid: 7b2b58c6-55cd-4682-a5d7-43874e70920d
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 53e90448d5e7a24f4904f9c4ea02ac041531ce02
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Propriétés MSBuild prises en charge par SharePoint
  N’importe quel [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] propriété définie dans le fichier Microsoft.VisualStudio.SharePoint.targets, le fichier projet ou le fichier utilisateur de projet peut être utilisée dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projets SharePoint. En plus courantes [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] propriétés fournies par le projet, SharePoint définit des propriétés supplémentaires qui sont spécifiques aux projets SharePoint.  
  
 Pour obtenir la liste de commun [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] propriétés, consultez [propriétés communes des projets MSBuild](http://go.microsoft.com/fwlink/?LinkID=168687). Pour obtenir une liste complète des propriétés prises en charge par votre langage de programmation, recherchez dans le fichier .targets, le fichier projet (.csproj ou .vbproj) ou le fichier utilisateur de projet (csproj.user ou. vbproj.user).  
  
## <a name="msbuild-properties-specific-to-sharepoint"></a>Propriétés MSBuild spécifiques à SharePoint  
 Le tableau suivant répertorie [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] propriétés qui s’appliquent spécifiquement aux projets SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. D’autres propriétés existent, mais elles sont à un usage interne.  
  
|Nom de la propriété|Description|  
|-------------------|-----------------|  
|SharePointSiteUrl|Chaîne qui représente le [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] sur le site SharePoint.|  
|SandboxedSolution|Valeur booléenne qui indique si la solution est une solution bac à sable.|  
|ActiveDeploymentConfiguration|La configuration de déploiement active.|  
|IncludeAssemblyInPackage|Valeur booléenne qui indique si l’assembly est inclus dans le fichier de package.|  
|PreDeploymentCommand|Valeur de chaîne qui représente la commande à exécuter dans l’étape de commande de prédéploiement.|  
|PostDeploymentCommand|Valeur de chaîne qui représente la commande à exécuter dans l’étape de commande de post-déploiement.|  
|CustomBeforeSharePointTargets|Chaîne qui représente le chemin d’accès d’un [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] fichier de cibles. Si le fichier cible existe et est défini, il est importé avant toutes les données de cibles SharePoint. Cette propriété vous permet de personnaliser le processus par prédéfinissant propriétés relatives à l’empaquetage sans modifier le fichier de cibles SharePoint expédié, mais le fichier de cibles s’applique toujours à tous les projets SharePoint.|  
|CustomAfterSharePointTargets|Chaîne qui représente le chemin d’accès d’un [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] fichier de cibles. Si le fichier cible existe et est défini, il est importé après toutes les données cibles SharePoint. Cette propriété vous permet de personnaliser le processus en remplaçant les propriétés liées à la mise en package et les cibles sans avoir à modifier le fichier de cibles SharePoint expédié, mais le fichier de cibles s’applique toujours à tous les projets SharePoint.|  
|LayoutPath|Chaîne qui représente le répertoire racine où chacun des fichiers à empaqueter sont temporairement placés avant d’être ajoutés au fichier .wsp. Ce chemin d’accès peut être utile de savoir quand vous remplacez les cibles BeforeLayout et AfterLayout pour ajouter, supprimer ou modifier des fichiers à empaqueter, car vous pouvez l’utiliser pour modifier le contenu du fichier .wsp.|  
|BasePackagePath|Chaîne qui représente le dossier dans lequel le package est placé. Cette valeur utilise le répertoire de sortie du projet, telles que le dossier Bin\Debug.|  
|PackageExtension|Chaîne qui représente l’extension de nom de fichier à ajouter au package. La valeur par défaut est wsp.|  
|AssemblyDeploymentTarget|Chaîne qui représente l’emplacement où l’assembly de projet est déployé sur le serveur SharePoint. Sa valeur est GlobalAssemblyCache (valeur par défaut) ou WebApplication. Cette propriété peut également être définie dans la fenêtre Propriétés.|  
|PackageWithValidation|Valeur booléenne qui spécifie si la validation est effectuée avant l’empaquetage. Cette propriété vous permet d’ignorer les erreurs de validation lors de la génération de Packages.|  
|ValidatePackageDependsOn|Chaîne qui définit des cibles supplémentaires à exécuter avant la cible ValidatePackage.|  
|TokenReplacementFileExensions|Chaîne qui définit les fichiers dont les jetons sont remplacés lors de l’empaquetage.|  
  
## <a name="using-msbuild-properties-in-the-properties-page"></a>Dans la Page de propriétés à l’aide de propriétés MSBuild  
 Pour une flexibilité, au lieu d’utiliser des chaînes codées en dur dans le **ligne de commande de prédéploiement** et **ligne de commande de post-déploiement** zones sur la page Propriétés SharePoint, vous pouvez utiliser SharePoint propriétés en tant qu’arguments. Par exemple, au lieu de spécifier des spécifique [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] chaîne pour le site SharePoint, vous pouvez utiliser `$(SharePointSiteUrl)`.  
  
> [!NOTE]  
>  Vous pouvez utiliser la [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] syntaxe de variable `$(` *propertyName* `)` ou la syntaxe de variable d’environnement `%` *propertyName* `%` Pour spécifier une propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur MSBuild](/visualstudio/msbuild/msbuild-reference)  
  
  