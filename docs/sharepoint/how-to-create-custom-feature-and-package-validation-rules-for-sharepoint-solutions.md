---
title: Créer des validations de fonctionnalités et de packages pour les solutions SharePoint
titleSuffix: ''
description: Créez des règles de validation personnalisées pour vérifier le package de solution généré par Visual Studio ou pour vérifier l’intégralité d’une fonctionnalité.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ee6b27b92f1c79bfda95ba3d6dce7dbdce4a6fac
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216564"
---
# <a name="create-feature-and-package-validations-for-sharepoint-solutions"></a>Créer des validations de fonctionnalités et de packages pour les solutions SharePoint

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

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite des références aux assemblys suivants :

- Microsoft. VisualStudio. SharePoint.

- System. ComponentModel. composition.

## <a name="deploy-the-extension"></a>Déployer l’extension
 Pour déployer l’extension, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Étendre le déploiement et l’empaquetage SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
