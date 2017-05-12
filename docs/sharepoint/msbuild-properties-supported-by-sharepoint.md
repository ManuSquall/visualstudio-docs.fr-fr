---
title: "Propri&#233;t&#233;s MSBuild prises en charge par SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, MSBuild (propriétés)"
ms.assetid: 7b2b58c6-55cd-4682-a5d7-43874e70920d
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Propri&#233;t&#233;s MSBuild prises en charge par SharePoint
  Toute propriété [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] définie dans le fichier Microsoft.VisualStudio.SharePoint.targets, le fichier projet ou le fichier utilisateur de projet peut être utilisée dans les projets [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint.  En plus des propriétés [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] communes fournies par le projet, SharePoint définit des propriétés supplémentaires qui sont spécifiques aux projets SharePoint.  
  
 Pour une liste de propriétés [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] courantes, consultez [Propriétés courantes de Projet MSBuild](http://go.microsoft.com/fwlink/?LinkID=168687).  Pour obtenir la liste complète des propriétés prises en charge par votre langage de programmation, consultez le fichier .targets, le fichier projet \(.csproj ou .vbproj\) ou le fichier utilisateur de projet \(csproj.user ou .vbproj.user\).  
  
## Propriétés MSBuild spécifiques à SharePoint  
 Le tableau suivant répertorie des propriétés [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] qui s'appliquent spécifiquement aux projets SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  D'autres propriétés existent, mais elles sont destinées à un usage interne.  
  
|Nom de la propriété|Description|  
|-------------------------|-----------------|  
|SharePointSiteUrl|Chaîne qui représente l'[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] pour le site SharePoint.|  
|SandboxedSolution|Valeur booléenne qui indique si la solution est une solution bac à sable \(sandbox\).|  
|ActiveDeploymentConfiguration|Configuration de déploiement active.|  
|IncludeAssemblyInPackage|Valeur booléenne qui indique si l'assembly est inclus dans le fichier de package.|  
|PreDeploymentCommand|Valeur de chaîne qui représente la commande à exécuter dans l'étape de commande de prédéploiement.|  
|PostDeploymentCommand|Valeur de chaîne qui représente la commande à exécuter dans l'étape de commande de post\-déploiement.|  
|CustomBeforeSharePointTargets|Chaîne qui représente le chemin d'accès d'un fichier de cibles [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)].  Si le fichier de cibles existe et est défini, il est importé avant toutes les données de cibles SharePoint.  Cette propriété vous permet de personnaliser le processus d'empaquetage en prédéfinissant les propriétés relatives à l'empaquetage sans modifier le fichier de cibles SharePoint expédié ; le fichier de cibles s'applique cependant encore à tous les projets SharePoint.|  
|CustomAfterSharePointTargets|Chaîne qui représente le chemin d'accès d'un fichier de cibles [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)].  Si le fichier de cibles existe et est défini, il est importé après toutes les données de cibles SharePoint.  Cette propriété vous permet de personnaliser le processus d'empaquetage en substituant les propriétés relatives à l'empaquetage et les cibles sans avoir à modifier le fichier de cibles SharePoint expédié ; le fichier de cibles s'applique cependant encore à tous les projets SharePoint.|  
|LayoutPath|Chaîne qui représente le répertoire racine dans lequel chacun des fichiers à empaqueter est temporairement placé avant d'être ajouté au fichier .wsp.  Ce chemin d'accès peut être utile pour savoir quand substituer les cibles BeforeLayout et AfterLayout pour ajouter, supprimer ou modifier des fichiers à empaqueter, car il vous permet de modifier le contenu du fichier .wsp.|  
|BasePackagePath|Chaîne qui représente le dossier dans lequel le package est placé.  Cette valeur utilise le répertoire de sortie du projet, tel que Bin\\Debug.|  
|PackageExtension|Chaîne qui représente l'extension de nom de fichier à ajouter au package.  La valeur par défaut est wsp.|  
|AssemblyDeploymentTarget|Chaîne qui représente l'emplacement dans lequel l'assembly de projet est déployé sur le serveur SharePoint.  Sa valeur est GlobalAssemblyCache \(valeur par défaut\) ou WebApplication.  Cette propriété peut également être définie dans la fenêtre Propriétés.|  
|PackageWithValidation|Valeur booléenne qui spécifie si la validation est exécutée avant l'empaquetage.  Cette propriété vous permet d'ignorer les erreurs de validation lors de la génération des packages.|  
|ValidatePackageDependsOn|Chaîne qui définit des cibles supplémentaires à exécuter avant la cible ValidatePackage.|  
|TokenReplacementFileExensions|Chaîne qui définit les fichiers dont les jetons sont remplacés au moment de l'empaquetage.|  
  
## Utilisation de propriétés MSBuild sur la page des propriétés  
 Pour des raisons de flexibilité, au lieu d'utiliser des chaînes codées en dur dans les zones **Ligne de commande de prédéploiement** et **Ligne de commande de post\-déploiement** dans la page Propriétés SharePoint, vous pouvez utiliser les propriétés SharePoint comme arguments.  Par exemple, plutôt que d'indiquer une chaîne [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] spécifique pour le site SharePoint, vous pouvez utiliser `$(SharePointSiteUrl)`.  
  
> [!NOTE]  
>  Vous pouvez utiliser la syntaxe de variable [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] `$(`*propertyName*`)` ou la syntaxe de variable d'environnement `%`*propertyName*`%` pour spécifier une propriété.  
  
## Voir aussi  
 [MSBuild Reference](../msbuild/msbuild-reference.md)  
  
  