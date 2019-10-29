---
title: Propriétés MSBuild prises en charge par SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5470160c6b0af1af39238a14319ad497e1541a43
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985167"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Propriétés MsBuild prises en charge par SharePoint
  Toute propriété [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] définie dans le fichier Microsoft. VisualStudio. SharePoint. targets, le fichier projet ou le fichier utilisateur du projet peut être utilisée dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projets SharePoint. Outre les propriétés de [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] courantes fournies par le projet, SharePoint définit des propriétés supplémentaires spécifiques aux projets SharePoint.

 Pour obtenir la liste des propriétés de [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] courantes, consultez [Propriétés de projet MSBuild courantes](/previous-versions/dotnet/netframework-4.0/bb629394(v=vs.100)). Pour obtenir la liste complète des propriétés prises en charge par votre langage de programmation, recherchez dans le fichier *. targets* , le fichier projet ( *. csproj* ou *. vbproj*) ou le fichier utilisateur du projet (*csproj. User* ou *. vbproj. User*).

## <a name="msbuild-properties-specific-to-sharepoint"></a>Propriétés MsBuild spécifiques à SharePoint
 Le tableau suivant répertorie [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] propriétés qui s’appliquent spécifiquement aux projets SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. D’autres propriétés existent, mais elles sont destinées à un usage interne.

|Nom de propriété|Description|
|-------------------|-----------------|
|SharePointSiteUrl|Chaîne qui représente la [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] au site SharePoint.|
|SandboxedSolution|Valeur booléenne qui indique si la solution est une solution bac à sable (sandbox).|
|ActiveDeploymentConfiguration|Configuration de déploiement active.|
|IncludeAssemblyInPackage|Valeur booléenne qui indique si l’assembly est inclus dans le fichier de package.|
|PreDeploymentCommand|Valeur de chaîne qui représente la commande à exécuter dans l’étape de commande de prédéploiement.|
|PostDeploymentCommand|Valeur de chaîne qui représente la commande à exécuter dans l’étape de commande de démarrage.|
|CustomBeforeSharePointTargets|Chaîne qui représente le chemin d’accès d’un fichier de cibles [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]. Si le fichier de cibles existe et est défini, il est importé avant les données SharePoint cibles. Cette propriété vous permet de personnaliser le processus de package en prédéfinissant les propriétés liées à l’empaquetage sans modifier le fichier de cibles SharePoint livrées, mais le fichier de cibles s’applique toujours à tous les projets SharePoint.|
|CustomAfterSharePointTargets|Chaîne qui représente le chemin d’accès d’un fichier de cibles [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]. Si le fichier de cibles existe et est défini, il est importé après toutes les données de cibles SharePoint. Cette propriété vous permet de personnaliser le processus de package en substituant les propriétés et les cibles liées à l’empaquetage sans avoir à modifier le fichier de cibles SharePoint livrées, mais le fichier de cibles s’applique toujours à tous les projets SharePoint.|
|LayoutPath|Chaîne qui représente le répertoire racine dans lequel chaque fichier à empaqueter est placé temporairement avant d’être ajouté au fichier *. wsp* . Ce chemin d’accès peut être utile pour savoir quand vous substituez les cibles BeforeLayout et AfterLayout pour ajouter, supprimer ou modifier des fichiers à empaqueter, car vous pouvez l’utiliser pour modifier le contenu du fichier *. wsp* .|
|BasePackagePath|Chaîne qui représente le dossier dans lequel le package est placé. Cette valeur utilise le répertoire de sortie du projet, par exemple Bin\Debug.|
|PackageExtension|Chaîne qui représente l’extension de nom de fichier à ajouter au package. La valeur par défaut est wsp.|
|AssemblyDeploymentTarget|Chaîne qui représente l’emplacement où l’assembly de projet est déployé sur le serveur SharePoint. Sa valeur est GlobalAssemblyCache (valeur par défaut) ou WebApplication. Cette propriété peut également être définie dans la Fenêtre Propriétés.|
|PackageWithValidation|Valeur booléenne qui spécifie si la validation est effectuée avant le Packaging. Cette propriété vous permet d’ignorer les erreurs de validation lors de la génération de packages.|
|ValidatePackageDependsOn|Chaîne qui définit les cibles supplémentaires à exécuter avant la cible ValidatePackage.|
|TokenReplacementFileExensions|Chaîne qui définit les fichiers dont les jetons sont remplacés pendant l’empaquetage.|

## <a name="use-msbuild-properties-in-the-properties-page"></a>Utiliser les propriétés MsBuild dans la page Propriétés
 Pour plus de flexibilité, au lieu d’utiliser des chaînes codées en dur dans les zones ligne de **commande de prédéploiement** et ligne de commande de pré **-déploiement** dans la page Propriétés de SharePoint, vous pouvez utiliser les propriétés SharePoint comme arguments. Par exemple, au lieu de spécifier une chaîne de [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] spécifique pour le site SharePoint, vous pouvez utiliser à la place `$(SharePointSiteUrl)`.

> [!NOTE]
> Vous pouvez utiliser la syntaxe de variable [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] `$(`*propertyname*`)` ou la syntaxe de variable d’environnement `%`*PropertyName*`%` pour spécifier une propriété.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)