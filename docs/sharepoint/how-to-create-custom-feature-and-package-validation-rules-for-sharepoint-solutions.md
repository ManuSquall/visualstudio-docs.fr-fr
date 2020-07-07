---
title: 'Solutions SharePoint : créer une fonctionnalité personnalisée, règles de validation du package'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f731b6af2ada8caddb84be5561d7f6dc304e7bbd
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016912"
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>Comment : créer des règles de validation de fonctionnalité et de package personnalisées pour les solutions SharePoint
  Vous pouvez créer des règles de validation personnalisées pour vérifier le package de solution généré par Visual Studio. Vous pouvez effectuer une validation complète sur l’intégralité d’une fonctionnalité ou d’un package en sélectionnant **valider** dans le menu contextuel d’un package ou d’une fonctionnalité dans le **PackagingExplorer**. La validation partielle est effectuée quand vous ajoutez de nouveaux éléments de projet SharePoint ou des fonctionnalités au projet pour déterminer si le package ou la fonctionnalité est dans un état valide.

### <a name="to-create-a-custom-package-validation-rule"></a>Pour créer une règle de validation de package personnalisée

1. Créez un projet de bibliothèque de classes.

2. Ajoutez des références aux assemblys suivants :

    - Microsoft. VisualStudio. SharePoint

    - System.ComponentModel.Composition

3. Créez une classe qui implémente l’une des interfaces suivantes :

    - Pour créer une règle de validation de package, implémentez l' <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> interface.

    - Pour créer une règle de validation de fonctionnalité, implémentez l' <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> interface.

4. Ajoutez <xref:System.ComponentModel.Composition.ExportAttribute> à la classe. Cet attribut permet à Visual Studio de découvrir et de charger votre règle de validation. Transmettez <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> le <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> type ou au constructeur d’attribut.

## <a name="example"></a>Exemple
 L’exemple de code suivant montre comment créer une règle de validation de fonctionnalité personnalisée.

 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite des références aux assemblys suivants :

- Microsoft. VisualStudio. SharePoint.

- System. ComponentModel. composition.

## <a name="deploy-the-extension"></a>Déployer l’extension
 Pour déployer l’extension, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Étendre le déploiement et l’empaquetage SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
