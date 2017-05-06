---
title: "Int&#233;gration de donn&#233;es m&#233;tiers dans SharePoint"
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
  - "BDC (développement SharePoint dans Visual Studio), agréger des données"
  - "BDC (développement SharePoint dans Visual Studio), données métiers"
  - "BDC (développement SharePoint dans Visual Studio), créer un modèle"
  - "BDC (développement SharePoint dans Visual Studio), données"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), agréger des données"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), données métiers"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), créer un modèle"
  - "service de connectivité de données métiers (développement SharePoint dans Visual Studio), données"
ms.assetid: e092e3d6-2c5f-4060-ae86-d37db8967559
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Int&#233;gration de donn&#233;es m&#233;tiers dans SharePoint
  Vous avez la possibilité d'ajouter des données métiers dans SharePoint.  Celles\-ci peuvent provenir d'applications serveur principales, telles que [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel et SAP, ou d'un service Web.  Les utilisateurs peuvent afficher, ajouter, mettre à jour ou supprimer des données métiers en utilisant des listes externes ou des composants WebPart de données métiers dans SharePoint. Les utilisateurs peuvent également accéder à ces données hors connexion dans une application Microsoft Office telle que Microsoft Outlook.  Pour plus d'informations, consultez[Où vous pouvez afficher les données externes](http://go.microsoft.com/fwlink/?LinkId=169295).  
  
 Pour intégrer des données dans SharePoint, vous devez commencer par créer un modèle pour le service BDC \(Business Data Connectivity\).  Le service BDC est une application dans SharePoint prévue pour stocker les informations relatives aux données des applications métier.  Pour plus d'informations, consultez [Service name \(BDC\) de business data connectivity](http://go.microsoft.com/fwlink/?LinkID=169276).  
  
## Modèles dans Visual Studio  
 Les modèles dans Visual Studio permettent d'écrire le code personnalisé nécessaire pour extraire et mettre à jour les données de sources de données principales.  Il est possible, en outre, de cumuler les données à partir de plusieurs sources de données.  Vous pouvez, par exemple, afficher une liste de clients combinant les données d'une base de données [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] et d'un service Web.  
  
 Vous êtes libre également d'importer des modèles déjà déployés sur SharePoint.  Après avoir importé un modèle, vous pouvez ajouter du code personnalisé ou vous contenter d'utiliser Visual Studio pour créer un package et déployer le modèle sur plusieurs batteries de serveurs SharePoint.  Pour plus d'informations, consultez [Création d'un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## Conception d'un modèle dans Visual Studio  
 Vous avez la possibilité de concevoir un modèle à l'aide d'un concepteur et de plusieurs fenêtres Outil.  Visual Studio génère le code XML du modèle en conséquence.  Pour plus d'informations, consultez [Vue d'ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
 Un modèle contient des entités et des méthodes.  
  
### Entités  
 Une entité décrit une collection de champs.  Une entité peut représenter, par exemple, une table dans une base de données.  Une entité s'affiche sous la forme d'un type de contenu externe dans SharePoint.  Pour plus d'informations sur les types de contenu externes, consultez [Que sont les types de contenu externes ?](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### Méthodes  
 Une méthode offre aux utilisateurs d'un type de contenu externe la possibilité d'intervenir sur les champs d'une entité.  La méthode Updater pourrait leur permettre, par exemple, de modifier l'adresse et la date de naissance d'un client où `Address` et `BirthDate` correspondent aux champs de l'entité `Customer`.  
  
 Visual Studio génère un fichier de code de service pour chaque entité de votre modèle.  Lorsque vous ajoutez une méthode à votre modèle, Visual Studio génère une méthode correspondante dans le fichier de code de service.  Pensez à insérer le code dans chaque méthode pour effectuer la tâche appropriée.  Si vous ajoutez, par exemple, une méthode Creator au modèle, Visual Studio génère une méthode Creator dans votre fichier de code de service.  Cette méthode est appelée par le service BDC dès qu'un utilisateur clique sur le bouton **Nouvel élément** dans une liste basée sur le modèle.  Il convient, par conséquent, d'incorporer le code à la méthode Creator prévue pour ajouter de nouvelles données à une source de données.  Pour plus d'informations, consultez [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Création d'un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)|Explique comment créer un modèle ou importer un modèle exporté depuis SharePoint.|  
|[Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)|Explique comment concevoir les éléments d'un modèle à l'aide des outils de conception Visual Studio.|  
|[Quand utiliser le concepteur de SharePoint plutôt que Visual Studio pour générer des solutions à BCS](http://go.microsoft.com/fwlink/?LinkID=183448)|Vous aide à décider si vous devez utiliser Visual Studio ou SharePoint Designer pour créer un modèle pour le BDC.|  
  
  