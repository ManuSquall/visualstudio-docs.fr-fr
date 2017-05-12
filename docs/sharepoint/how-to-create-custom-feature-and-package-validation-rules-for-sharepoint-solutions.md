---
title: "How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, extending deployment"
  - "SharePoint development in Visual Studio, validation rules"
ms.assetid: 17e818f8-0f3a-4a96-a6fc-1634ddb4825d
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions
  Vous pouvez créer des règles de validation personnalisées pour vérifier le package de solution généré par Visual Studio.  Vous pouvez exécuter la validation complète sur une fonctionnalité ou un package entier en sélectionnant **Valider** dans le menu contextuel d'un package ou d'une fonctionnalité dans l'**Explorateur de package**.  La validation partielle est exécutée lorsque vous ajoutez de nouveaux éléments de projet SharePoint ou de nouvelles fonctionnalités au projet, afin de vérifier la validité de l'état du package ou de la fonctionnalité.  
  
### Pour créer une règle de validation de package personnalisée  
  
1.  Créez un projet Bibliothèque de classes.  
  
2.  Ajoutez des références aux assemblys suivants :  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Créez une classe qui implémente l'une des interfaces suivantes :  
  
    -   Pour créer une règle de validation de package, implémentez l'interface <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>.  
  
    -   Pour créer une règle de validation de fonctionnalité, implémentez l'interface <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>.  
  
4.  Ajoutez l'attribut <xref:System.ComponentModel.Composition.ExportAttribute> à la classe.  Cet attribut permet à Visual Studio de découvrir et de charger votre règle de validation.  Communiquez le type <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> or <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> au constructeur de l'attribut.  
  
## Exemple  
 L'exemple de code suivant montre comment créer une règle de validation de fonctionnalité personnalisée.  
  
 [!code-csharp[SPExtensibility.FeatureValidation#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.featurevalidation/cs/extension/customfeaturevalidationrule.cs#1)]
 [!code-vb[SPExtensibility.FeatureValidation#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.featurevalidation/vb/extension/customvalidationrule.vb#1)]  
  
## Compilation du code  
 Cet exemple nécessite des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint.  
  
-   System.ComponentModel.Composition.  
  
## Déploiement de l'extension  
 Pour déployer l'extension, créez un package d'extension [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) pour l'assembly et tous les autres fichiers que vous voulez distribuer avec l'extension.  Pour plus d'informations, consultez [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Voir aussi  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  