---
title: "Fusionner du code&#160;XML dans des manifestes de fonctionnalit&#233;s et de packages"
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
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, empaqueter"
ms.assetid: fc1cbd2a-0166-4f2f-a81b-4dac2fa7b0f3
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Fusionner du code&#160;XML dans des manifestes de fonctionnalit&#233;s et de packages
  Les fonctionnalités et les packages sont définis par les fichiers manifeste [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)].  Ces manifestes ajoutés au package sont une combinaison des données générées par les concepteurs et un fichier [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] personnalisé que les utilisateurs entrent dans le modèle de manifeste.  Lors de l'empaquetage, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fusionne les instructions [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] personnalisées avec le [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] fourni par le concepteur pour former le fichier manifeste [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ajouté au package.  Les éléments semblables, avec les exceptions notées ultérieurement dans Exceptions de fusion, sont fusionnés pour éviter des erreurs de validation [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] après le déploiement des fichiers sur SharePoint, et pour faire en sorte que les fichiers manifeste soient plus petits et plus efficaces.  
  
## Modification des manifestes  
 Vous ne pouvez pas modifier directement les fichiers manifeste ajoutés au package tant que vous n'avez pas désactivé les concepteurs de fonctionnalités ou de packages.  Toutefois, vous pouvez ajouter manuellement des éléments [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] personnalisés au modèle de manifeste via les concepteurs de fonctionnalités et de packages ou l'éditeur [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)].  Pour plus d’informations, consultez [Comment : personnaliser une fonctionnalité SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) et [Comment : personnaliser un package de solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
## Processus de fusion des manifestes de fonctionnalité et de package  
 Lors de la combinaison d'éléments personnalisés avec des éléments fournis par le concepteur, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilise le processus suivant.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vérifie si chaque élément a une valeur de clé unique.  Si un élément n'a aucune valeur de clé unique, elle est ajoutée au fichier de manifeste ajouté au package.  De même, les éléments qui ont plusieurs clés peuvent être fusionnés.  Par conséquent, ils sont ajoutés au fichier manifeste.  
  
 Si un élément a une clé unique, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compare les valeurs des clés de concepteur et personnalisée.  Si les valeurs correspondent, elles fusionnent en une seule.  Si elles diffèrent, la valeur de clé de concepteur est ignorée et la valeur de clé personnalisée est utilisée.  Les collections sont également fusionnées.  Par exemple, si le [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] généré par le concepteur et le [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] personnalisé contiennent chacun une collection d'assemblys, le manifeste ajouté au package contient une seule collection d'assemblys.  
  
## Exceptions de fusion  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fusionne la plupart des éléments [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] de concepteur avec des éléments [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] personnalisés semblables, à condition qu'ils aient un seul attribut d'identification unique.  Toutefois, certains éléments ne possèdent pas l'identificateur unique obligatoire pour la fusion du [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)].  Ces éléments sont appelés *exceptions de fusion*.  Dans ce cas, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ne fusionne pas les éléments [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] personnalisés avec les éléments [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] fournis par le concepteur, mais les ajoute au fichier manifeste ajouté au package.  
  
 Voici une liste d'exceptions de fusion pour les fichiers manifeste [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] de fonctionnalité et de package.  
  
|Concepteur|XML \(élément\)|  
|----------------|---------------------|  
|Concepteur de fonctionnalités|ActivationDependency|  
|Concepteur de fonctionnalités|UpgradeAction|  
|Concepteur de packages|SafeControl|  
|Concepteur de packages|CodeAccessSecurity|  
  
## Éléments de manifeste de fonctionnalité  
 Le tableau suivant est une liste de tous les éléments de manifeste de fonctionnalité qui peuvent être fusionnés et de leur clé unique utilisée pour la mise en correspondance.  
  
|Nom de l'élément|Clé unique|  
|----------------------|----------------|  
|Fonctionnalité \(tous les attributs\)|*Attribute Name* \(chaque nom d'attribut de l'élément de fonctionnalité est une clé unique.\)|  
|ElementFile|Emplacement|  
|ElementManifests\/ElementManifest|Emplacement|  
|Properties\/Property|Clé|  
|CustomUpgradeAction|Nom|  
|CustomUpgradeActionParameter|Nom|  
  
> [!NOTE]  
>  Étant donné que la seule méthode pour modifier l'élément CustomUpgradeAction consiste à utiliser l'éditeur [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] personnalisé, l'absence de fusion n'a pas de conséquences importantes.  
  
## Éléments de manifeste de package  
 Le tableau suivant est une liste de tous les éléments de manifeste de package qui peuvent être fusionnés et de leur clé unique utilisée pour la mise en correspondance.  
  
|Nom de l'élément|Clé unique|  
|----------------------|----------------|  
|Solution \(tous les attributs\)|*Attribute Name* \(chaque nom d'attribut de l'élément de solution est une clé unique.\)|  
|ApplicationResourceFiles\/ApplicationResourceFile|Emplacement|  
|Assemblies\/Assembly|Emplacement|  
|ClassResources\/ClassResource|Emplacement|  
|DwpFiles\/DwpFile|Emplacement|  
|FeatureManifests\/FeatureManifest|Emplacement|  
|Resources\/Resource|Emplacement|  
|RootFiles\/RootFile|Emplacement|  
|SiteDefinitionManifests\/SiteDefinitionManifest|Emplacement|  
|WebTempFile|Emplacement|  
|TemplateFiles\/TemplateFile|Emplacement|  
|SolutionDependency|SolutionID|  
  
## Ajout manuel de fichiers déployés  
 Certains manifestes d'élément, tels que ApplicationResourceFile et DwpFiles, spécifient un emplacement qui inclut un nom de fichier.  Toutefois, l'ajout d'une entrée de nom de fichier au modèle de manifeste n'ajoute pas le fichier sous\-jacent au package.  Vous devez ajouter le fichier au projet pour l'inclure dans le package et définir sa propriété Deployment Type en conséquence.  
  
## Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Génération et débogage de solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  