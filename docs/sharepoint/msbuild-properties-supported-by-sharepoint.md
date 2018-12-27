---
title: Propriétés MSBuild prises en charge par SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 55561d570605cfd5690fc0459444b2fbadeca51a
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684806"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Propriétés MsBuild prises en charge par SharePoint
  N’importe quel [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] propriété définie dans le fichier Microsoft.VisualStudio.SharePoint.targets, le fichier projet ou le fichier utilisateur de projet peut être utilisée dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projets SharePoint. En plus courantes [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] propriétés fournies par le projet, SharePoint définit des propriétés supplémentaires qui sont spécifiques aux projets SharePoint.  
  
 Pour obtenir la liste de commun [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] propriétés, consultez [propriétés communes des projets MSBuild](http://go.microsoft.com/fwlink/?LinkID=168687). Pour obtenir une liste complète des propriétés prises en charge par votre langage de programmation, recherchez dans le *.targets* , le fichier projet (*.csproj* ou *.vbproj*), ou l’utilisateur de projet de fichier () *csproj.user* ou *. vbproj.user*).  
  
## <a name="msbuild-properties-specific-to-sharepoint"></a>Propriétés MsBuild spécifiques à SharePoint
 Le tableau suivant répertorie [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] propriétés qui s’appliquent spécifiquement aux projets SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. D’autres propriétés existent, mais ils sont à usage interne.  
  
|Nom de la propriété|Description|  
|-------------------|-----------------|  
|SharePointSiteUrl|Chaîne qui représente le [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] sur le site SharePoint.|  
|SandboxedSolution|Valeur booléenne qui indique si la solution est une solution bac à sable.|  
|ActiveDeploymentConfiguration|La configuration de déploiement active.|  
|IncludeAssemblyInPackage|Valeur booléenne qui indique si l’assembly est inclus dans le fichier de package.|  
|PreDeploymentCommand|Valeur de chaîne qui représente la commande à exécuter dans l’étape de commande de prédéploiement.|  
|PostDeploymentCommand|Valeur de chaîne qui représente la commande à exécuter dans l’étape de commande de post-déploiement.|  
|CustomBeforeSharePointTargets|Chaîne qui représente le chemin d’accès d’un [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] fichier de cibles. Si le fichier de cibles existe et est défini, il est importé avant toutes les données cibles SharePoint. Cette propriété vous permet de personnaliser le processus de package en prédéfinissant des propriétés relatives à l’empaquetage sans modifier le fichier de cibles SharePoint expédié, mais le fichier de cibles s’applique toujours à tous les projets SharePoint.|  
|CustomAfterSharePointTargets|Chaîne qui représente le chemin d’accès d’un [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] fichier de cibles. Si le fichier de cibles existe et est défini, il est importé après toutes les données de cibles SharePoint. Cette propriété vous permet de personnaliser le processus de package en substituant les propriétés relatives à l’empaquetage et les cibles sans avoir à modifier le fichier de cibles SharePoint expédié, mais le fichier de cibles s’applique toujours à tous les projets SharePoint.|  
|LayoutPath|Chaîne qui représente le répertoire racine où chacun des fichiers à empaqueter sont temporairement placés avant d’être ajoutés à la *.wsp* fichier. Ce chemin d’accès peut être utile de savoir lorsque vous substituez les cibles BeforeLayout et AfterLayout pour ajouter, supprimer ou modifier des fichiers à empaqueter, car vous pouvez l’utiliser pour modifier le contenu de la *.wsp* fichier.|  
|BasePackagePath|Chaîne qui représente le dossier dans lequel le package est placé. Cette valeur utilise le répertoire de sortie du projet, telles que Bin\Debug.|  
|PackageExtension|Chaîne qui représente l’extension de nom de fichier à ajouter au package. La valeur par défaut est wsp.|  
|AssemblyDeploymentTarget|Chaîne qui représente l’emplacement où l’assembly de projet est déployé sur le serveur SharePoint. Sa valeur est GlobalAssemblyCache (valeur par défaut) ou WebApplication. Cette propriété peut également être définie dans la fenêtre Propriétés.|  
|PackageWithValidation|Valeur booléenne qui spécifie si une validation est effectuée avant l’empaquetage. Cette propriété vous permet d’ignorer les erreurs de validation lors de la création de Packages.|  
|ValidatePackageDependsOn|Chaîne qui définit des cibles supplémentaires à exécuter avant la cible ValidatePackage.|  
|TokenReplacementFileExensions|Chaîne qui définit les fichiers qui ont les jetons sont remplacés lors de l’empaquetage.|  
  
## <a name="use-msbuild-properties-in-the-properties-page"></a>Utilisez les propriétés MsBuild dans la page de propriétés
 Pour une flexibilité, au lieu d’utiliser des chaînes codées en dur dans le **ligne de commande de prédéploiement** et **ligne de commande de post-déploiement** cases dans la page de propriétés de SharePoint, vous pouvez utiliser SharePoint propriétés en tant qu’arguments. Par exemple, au lieu de spécifier des spécifique [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] chaîne pour le site SharePoint, vous pouvez utiliser `$(SharePointSiteUrl)`.  
  
> [!NOTE]  
>  Vous pouvez utiliser la [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] syntaxe de variable `$(` *propertyName* `)` ou la syntaxe de variable d’environnement `%` *propertyName* `%` Pour spécifier une propriété.  
  
## <a name="see-also"></a>Voir aussi

- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)  