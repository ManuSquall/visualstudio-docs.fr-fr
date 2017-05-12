---
title: "Empaquetage et d&#233;ploiement de solutions SharePoint"
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
  - "déployer (développement SharePoint dans Visual Studio)"
  - "empaqueter (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, empaqueter et déployer"
ms.assetid: 39072fa7-9f94-49c0-9a67-cbcce0147e61
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Empaquetage et d&#233;ploiement de solutions SharePoint
  Une solution SharePoint est déployée, en général, sur un serveur SharePoint à l'aide d'un fichier de package de solution \(.wsp\).  Vous pouvez utiliser Visual Studio pour organiser vos éléments de projet SharePoint en fonctionnalités et créer un package dans le but de déployer vos fonctionnalités SharePoint.  
  
 Cette rubrique fournit les informations suivantes :  
  
-   [Création de fonctionnalités et de packages](#Creating)  
  
-   [Prise en charge des outils de fonctionnalité et d'empaquetage](#Tools)  
  
-   [Déploiement de solutions SharePoint](#Deploying)  
  
-   [Déploiement de fichiers dans les solutions SharePoint](#DeployingFiles)  
  
##  <a name="Creating"></a> Création de fonctionnalités et de packages  
 Servez\-vous de Visual Studio pour regrouper des éléments SharePoint connexes au sein d'une même *fonctionnalité*.  La fonctionnalité d'une définition de liste Contacts pourrait être constituée, par exemple, de l'instance de liste et de la définition de liste.  Il suffirait donc de combiner ces deux éléments dans une seule et même fonctionnalité à des fins de déploiement.  Pour plus d'informations sur les composants, consultez [Bloc de construction : Composants](http://go.microsoft.com/fwlink/?LinkID=169183).  
  
 Vous pouvez ensuite prévoir un package de solution SharePoint \(.wsp\) pour réunir plusieurs fonctionnalités, définitions de site, assemblys et autres fichiers dans un package unique contenant l'ensemble des fichiers dans le format requis par SharePoint pour déployer les fichiers sur le serveur.  Pour plus d'informations, consultez [Bloc de construction : Solutions](http://go.microsoft.com/fwlink/?LinkID=169186).  
  
##  <a name="Tools"></a> Prise en charge des outils de fonctionnalité et d'empaquetage  
 Les outils de développement SharePoint dans Visual Studio permettent d'organiser, de façon efficace, vos fichiers SharePoint en fonctionnalités et packages de solution afin de faciliter le déploiement.  Vous pouvez utiliser les outils suivants pour configurer les fonctionnalités et les packages de solution.  
  
-   Concepteur de fonctionnalités et Concepteur de packages.  
  
-   Explorateurs de package \(fenêtre Outil\).  
  
-   Explorateur de solutions.  
  
### Concepteur de fonctionnalités et Concepteur de packages  
 Le Concepteur de fonctionnalités permet de créer des fonctionnalités, de définir les portées et de configurer certaines fonctionnalités comme des dépendances.  Cet outil affiche également le fichier XML final qui décrit chaque fonctionnalité.  Pour plus d'informations, consultez [Création de fonctionnalités SharePoint](../sharepoint/creating-sharepoint-features.md).  
  
 Appliquez la fonctionnalité à un site Web spécifique ou à un groupe de sites Web en définissant sa *portée* dans le Concepteur de fonctionnalités.  Lorsqu'une fonctionnalité est activée pour un site Web en particulier, elle n'a d'effet que sur ce site Web.  Si une fonctionnalité est activée pour une collection de sites, les éléments de la fonctionnalité s'appliquent à l'ensemble de la collection.  Pour plus d'informations, consultez l'élément [Portée d'un Elément](http://go.microsoft.com/fwlink/?LinkID=169189)..  
  
 Si votre fonctionnalité repose sur d'autres fonctionnalités, pensez à définir une *dépendance d'activation de fonctionnalité* afin de marquer les fonctionnalités dépendantes avant de rendre votre fonctionnalité disponible.  Une dépendance d'activation de fonctionnalité vérifie si les fonctionnalités dépendantes sont déjà activées pour cette portée.  Pour plus d'informations, consultez [Dépendances et Portée d'Activation](http://go.microsoft.com/fwlink/?LinkID=169190).  
  
 Dans le Concepteur de packages, vous pouvez rassembler des éléments SharePoint dans un package de solution unique et préciser s'il est nécessaire ou non de réinitialiser le serveur Web pendant le déploiement.  Pour définir le type de serveur de déploiement, utilisez la fenêtre **Propriétés**.  Le concepteur génère également le fichier XML servant à décrire le contenu du package.  Pour plus d'informations, consultez [Création de packages de solution SharePoint](../sharepoint/creating-sharepoint-solution-packages.md).  
  
 Lors du déploiement, les Service Internet \(IIS\) sont arrêtés afin de copier les fichiers de la solution sur le serveur SharePoint.  Indiquez, à partir du Concepteur de packages dans Visual Studio, s'il est nécessaire ou non de redémarrer le serveur Web.  Pour déterminer si la solution est déployée sur un serveur Web frontal ou un serveur d'applications, utilisez la fenêtre **Propriétés**.  Pour plus d'informations, consultez [Élément de solution \(solution\)](http://go.microsoft.com/fwlink/?LinkID=169191).  
  
### Explorateur de package  
 Pour compléter le Concepteur de fonctionnalités et le Concepteur de packages, vous pouvez faire appel à l'Explorateur de package pour regrouper vos fichiers SharePoint dans les fonctionnalités et les packages.  Vous obtenez, en outre, une vue hiérarchique du package, des fonctionnalités, des éléments de projet SharePoint et des fichiers.  L'Explorateur de package est une fenêtre Outil permettant de réaliser les tâches suivantes :  
  
-   Ouvrir des éléments de projet et des fichiers SharePoint.  
  
-   Déplacer des éléments de projet SharePoint d'une fonctionnalité à une autre en les faisant glisser.  
  
-   Déplacer des éléments de projet et des fonctionnalités SharePoint d'un package à un autre en les faisant glisser.  
  
-   Ajouter une nouvelle fonctionnalité à un package.  
  
-   Ouvrir un Concepteur de fonctionnalités ou de packages.  
  
-   Valider les fonctionnalités et les packages.  
  
 Les outils de développement SharePoint dans Visual Studio obéissent à des règles de validation pour vous aider à vous assurer que les packages de solution sont formés correctement.  En outre, ces règles vérifient que le fichier de solution .wsp peut être correctement déployé et activé sur un serveur SharePoint.  Pour plus d'informations sur le schéma XML des composants, consultez [schémas des composants](http://go.microsoft.com/fwlink/?LinkID=169192).  
  
 Vous pouvez ajouter des règles de validation des fonctionnalités et des packages au système de projet SharePoint.  Pour plus d'informations, consultez [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
 Pour plus d'informations sur l'Explorateur de package, consultez [Comment : ajouter et supprimer des fonctionnalités et des éléments dans un package à l'aide de l'Explorateur de package](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
### Explorateur de solutions  
 Profitez de l'Explorateur de solutions pour faire défiler et ouvrir les fichiers du projet SharePoint.  Servez\-vous du menu contextuel dans l'Explorateur de solutions pour ajouter des fonctionnalités, des récepteurs d'événements de fonctionnalités et des ressources de fonctionnalités.  N'hésitez pas à utiliser le Concepteur de fonctionnalités et le Concepteur de packages pour configurer les fonctionnalités et les packages en vue du déploiement.  
  
##  <a name="Deploying"></a> Déploiement de solutions SharePoint  
 Après avoir personnalisé les fonctionnalités et les packages dans Visual Studio, vous pouvez créer un fichier .wsp afin de le déployer sur les serveurs SharePoint.  Servez\-vous, si nécessaire, de Visual Studio pour déboguer et tester le fichier .wsp uniquement sur le serveur SharePoint depuis l'ordinateur de développement.  Pour plus d'informations sur le déploiement de vos solutions SharePoint sur un serveur SharePoint distant, consultez [Déploiement d'une solution](http://go.microsoft.com/fwlink/?LinkID=169194).  
  
 Vous pouvez également personnaliser les étapes de déploiement sur l'ordinateur de développement.  Pour plus d'informations, consultez [Déploiement, publication et mise à niveau de packages de solutions SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
##  <a name="DeployingFiles"></a> Déploiement de fichiers dans les solutions SharePoint  
 En général, lorsque vous ajoutez un élément de projet SharePoint à votre solution SharePoint, tous les fichiers requis sont inclus.  Les fichiers qui peuvent être compilés \(fichiers de code\) sont intégrés dans l'assembly de sortie de la solution.  Toutefois, vous devrez peut\-être également ajouter des fichiers non compilables, par exemple des fichiers .xml, .txt, ou de ressources, à un projet SharePoint.  Ces fichiers ne sont pas empaquetés automatiquement dans votre solution.  Pour vous assurer qu'ils sont empaquetés, ajoutez les fichiers à un dossier mappé ou à un élément de projet SharePoint.  
  
 Une fois la solution déployée, les fichiers ajoutés aux dossiers mappés sont automatiquement copiés dans la ruche SharePoint.  Les fichiers ajoutés à un élément de projet SharePoint sont déployés vers l'emplacement spécifié dans la propriété **Emplacement de déploiement** pour chaque fichier, défini partiellement selon la propriété **Type de déploiement**.  Par défaut, la valeur de la propriété **Type de déploiement** est **NoDeployment**, qui signifie que le fichier n'est pas déployé avec la solution.  Vous devez attribuer une autre valeur à la propriété pour inclure le fichier dans le package.  
  
 Par exemple, pour ajouter un fichier .xml à un projet SharePoint, exécutez l'une des actions suivantes :  
  
-   Ajoutez un dossier mappé « Dispositions » SharePoint à votre projet.  Cette opération crée dans l'**Explorateur de solutions** un dossier nommé **Dispositions** qui contient un sous\-dossier pour le projet.  Ajoutez le fichier .xml dans le nouveau sous\-dossier.  Par défaut, le fichier est déployé vers le système de fichiers SharePoint sous..\\TEMPLATE\\LAYOUTS\\*Folder Name*\\.  Pour plus d'informations sur l'ajout de dossiers mappés, consultez [Comment : ajouter et supprimer des dossiers mappés](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
-   Ajoutez le fichier .xml au dossier d'un élément de projet SharePoint, puis modifiez la propriété **Type de déploiement** du fichier .xml de **NoDeployment** en un autre paramètre tel que **RootFile** ou **ElementFile**.  Le paramètre **Type de déploiement** approprié dépend du fichier et du projet.  Pour plus d'informations sur les paramètres de la propriété **Type de déploiement**, consultez [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).  
  
 Si un fichier ajouté ne s'applique pas à aucun projet en particulier dans la solution, vous pouvez ajouter un projet SharePoint vide à votre solution et y ajouter les fichiers supplémentaires.  Une autre possibilité pour le déploiement de fichiers vers SharePoint, en particulier vers la base de données de contenu, est d'ajouter un module au projet, puis d'ajouter les fichiers au module.  Pour plus d'informations, consultez [Utilisation de modules pour inclure des fichiers dans la solution](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## Voir aussi  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Génération et débogage de solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  