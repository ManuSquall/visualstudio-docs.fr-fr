---
title: "Comment : créer des règles de Validation de Package et de fonctionnalité personnalisée pour les Solutions SharePoint | Documents Microsoft"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: efc9cc2988125621212698576deeca1247e26a58
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>Comment : créer des règles de validation de fonctionnalité et de package personnalisées pour les solutions SharePoint
  Vous pouvez créer des règles de validation personnalisées pour vérifier que le package de solution généré par Visual Studio. Vous pouvez effectuer une validation complète sur une fonctionnalité complète ou un package en sélectionnant **Validate** dans le menu contextuel d’un package ou une fonctionnalité dans le **PackagingExplorer**. Validation partielle est exécutée lorsque vous ajoutez de nouveaux éléments de projet SharePoint ou des fonctionnalités pour le projet afin de déterminer si le Package ou la fonctionnalité est dans un état valide.  
  
### <a name="to-create-a-custom-package-validation-rule"></a>Pour créer une règle de validation de package personnalisé  
  
1.  Créez un projet de bibliothèque de classes.  
  
2.  Ajoutez des références aux assemblys suivants :  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Créez une classe qui implémente l’une des interfaces suivantes :  
  
    -   Pour créer une règle de validation de package, implémentez le <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> interface.  
  
    -   Pour créer une règle de validation de fonctionnalité, implémentez le <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> interface.  
  
4.  Ajouter le <xref:System.ComponentModel.Composition.ExportAttribute> à la classe. Cet attribut permet à Visual Studio détecter et charger votre règle de validation. Passez le <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> ou <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> type au constructeur d’attribut.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment créer une règle de validation de fonctionnalité personnalisée.  
  
 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint.  
  
-   System.ComponentModel.Composition.  
  
## <a name="deploying-the-extension"></a>Déploiement de l’Extension  
 Pour déployer l’extension, créez un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déploiement d’Extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de la création de packages et du déploiement SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  