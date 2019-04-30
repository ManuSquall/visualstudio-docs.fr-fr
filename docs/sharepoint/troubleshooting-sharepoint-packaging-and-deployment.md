---
title: Résolution des problèmes SharePoint Packaging and Deployment | Microsoft Docs
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VSTO.WorkflowDeployment.Troubleshooting
- VS.SharePointTools.Project.PackageRetraction
- VS.SharePointTools.Deployment.Troubleshooting
- VS.SharePointTools.Deploying.Troubleshooting
- VS.SharePointTools.Project.DeploymentTroubleshooting
- VS.SharePointTools.Project.SharePointNotInstalled
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
- SharePoint development in Visual Studio, troubleshooting
- SharePoint development in Visual Studio, deployment conflict resolution
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0c949f9a5d8c56f44e0754715d056b4d3837f76a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008347"
---
# <a name="troubleshoot-sharepoint-packaging-and-deployment"></a>Résoudre les problèmes de déploiement et empaquetage de SharePoint
  Cette rubrique couvre différents problèmes que vous pouvez rencontrer lorsque vous empaquetez et déployez des solutions SharePoint.

## <a name="enable-enhanced-debugging"></a>Activer le débogage amélioré
 Pour effectuer un diagnostic entre Visual Studio, SharePoint et d'autres couches, vous pouvez utiliser la clé de Registre EnableDiagnostics afin de consulter la trace de la pile. Pour plus d’informations, consultez [solutions SharePoint déboguer](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="add-project-output-to-the-solution-package"></a>Ajouter la sortie du projet au package de solution
 Vous pouvez ajouter la sortie de projet à un package via le Concepteur de packages. Toutefois, lorsque vous ajoutez la sortie de projet, assurez-vous que la plateforme du projet correspond à la plateforme de la solution SharePoint. Nous vous recommandons d’utiliser le **Any CPU** plateforme cible pour les assemblys que vous souhaitez déployer sur un serveur SharePoint. Pour plus d’informations, consultez [Page Compiler, Concepteur de projets &#40;Visual Basic&#41; ](../ide/reference/compile-page-project-designer-visual-basic.md) et [avancé de boîte de dialogue Paramètres du compilateur &#40;Visual Basic&#41;](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).

## <a name="validation-warnings-and-errors"></a>Erreurs et avertissements de validation
 Les outils de développement SharePoint dans Visual Studio exécutent des étapes de validation pour vérifier que le package de solution est correctement formé. Vous pouvez également créer des étapes de validation personnalisées pour vos fonctionnalités et vos packages. Pour plus d'informations, voir [Procédure : Créer des règles de validation pour les solutions SharePoint fonctionnalité personnalisée et un package](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="deployment-conflict-resolution"></a>Résolution des conflits de déploiement
 Lorsque vous déployez une solution SharePoint, vous pouvez être confronté à des collisions lorsqu'un élément sur le serveur a un nom, une URL ou un ID identique à celui ou celle d'un élément dans votre package de solution. Vous pouvez modifier le **Deployment Conflict Resolution** propriété à résoudre, signaler ou ignorer des collisions relatives des modules, les parties Web, les instances de listes et les types de contenu.

 Le tableau suivant montre les paramètres pour le **Deployment Conflict Resolution** propriété.

|Value|Description|
|-----------|-----------------|
|Automatique|Détecte les collisions et résout automatiquement les conflits.|
|Invite|Détecte les collisions et les signale au développeur avant de résoudre les conflits.|
|Aucun.|Ne détecte pas les collisions.|

## <a name="differences-between-f5-deployment"></a>Différences entre le déploiement F5
 Lorsque vous utilisez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pour déployer votre projet SharePoint sur le serveur SharePoint local à des fins de test et de débogage, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] exécute des opérations supplémentaires.

1. Réinitialisation des services IIS (Internet Information Services) pendant l'étape de déploiement.

2. Association automatique des flux de travail.

3. Définition de l’ordre d’activation des fonctionnalités en fonction de la hiérarchie du Concepteur de packages.

   Vous pouvez ajouter des étapes de déploiement personnalisées pour les autres modifications le **F5** comportement. Pour plus d’informations, consultez [Procédure pas à pas : Créer une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="delay-displaying-sharepoint-page-when-deploy-visual-web-part"></a>Différer l’affichage de page SharePoint lorsque déployez le composant visual web part
 L'affichage de la page SharePoint prend un certain temps lors du déploiement d'un composant Visual Web Part dans le dossier Bin sur [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)], [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] ou [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]. Si vous modifiez des fichiers dans un répertoire [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] de niveau supérieur, tel que le répertoire bin, l'application Web entière est recompilée. Cela peut différer de 25 secondes le rendu de la page SharePoint.

### <a name="error-message"></a>Message d'erreur
 Aucun.

### <a name="resolution"></a>Résolution
 Pour contourner ce problème, exécutez les étapes suivantes :

1. Installez la mise à jour KB967535 comme indiqué dans l’article du Support de Microsoft [corriger : Un correctif est disponible pour résoudre deux problèmes dans ASP.NET sur IIS 7.0 pour Windows Vista et Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=179055).

2. Ajoutez la ligne suivante au fichier Web.config :

    ```xml
    <compilation batch="false" optimizeCompilations="true">
    ```

## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>Déploiement de projet SharePoint échoue avec l’erreur « Échec de l’extraction du fichier .cab dans la solution »
 Si le nom d'un élément de projet SharePoint quelconque contient des parenthèses, le déploiement de la solution associée échoue avec une erreur.

### <a name="error-message"></a>Message d'erreur
 Erreur lors de l’étape de déploiement 'Ajouter une Solution' : Échec d’extraction du fichier .cab dans la solution.

### <a name="resolution"></a>Résolution
 Pour résoudre ce problème, supprimez les parenthèses dans les noms d'éléments de projet SharePoint.

## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>Erreur s’affiche lors du déploiement d’un composant visual web part sur un site sur une autre application web
 La première fois que vous déployez un élément Visual Web Part sur un site d'une application Web autre que celle dans laquelle il est actuellement déployé (en modifiant la propriété SiteUrl de l'élément Visual Web Part), vous obtenez une erreur.

### <a name="error-message"></a>Message d'erreur
 Erreur lors de l’étape de déploiement 'Ajouter une Solution' : Une fonctionnalité avec l’ID [#] a déjà été installée dans cette batterie de serveurs. Utilisez l’attribut force pour installer à nouveau la fonctionnalité de façon explicite.

### <a name="resolution"></a>Résolution
 Cette erreur est due au mode de retrait des fonctionnalités d'éléments Visual Web Part dans SharePoint. Pour déployer correctement le composant visual Web part, redéployez la solution en choisissant le **F5** clé.

## <a name="warning-appears-when-deploying-nested-user-controls"></a>Avertissement s’affiche lors du déploiement des contrôles utilisateur imbriqués
 Cet avertissement se produit lorsque vous déployez une solution SharePoint qui contient des contrôles utilisateur imbriqués, tels qu'un composant Visual Web Part qui contient un contrôle utilisateur ou un contrôle utilisateur qui contient un composant Visual Web Part ou un autre contrôle utilisateur. Cet avertissement se produit si vous ajoutez un contrôle à un concepteur en le faisant glisser à partir de la boîte à outils ou en utilisant la @Register directive dans la vue de Source.

### <a name="error-message"></a>Message d'erreur
 Avertissement 1 l’élément ' [*nom du contrôle*]' n’est pas un élément connu. Ceci peut se produire s'il existe une erreur de compilation dans le site Web ou si le fichier Web.config est manquant.

### <a name="resolution"></a>Résolution
 Si le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] système de projet n’a pas connaissance d’un contrôle utilisateur imbriqué, il ne peut pas fournir IntelliSense et il émet l’avertissement. Le système de projet n’a pas connaissance d’un contrôle utilisateur imbriqué si le projet n’est pas généré et le concepteur n’est pas fermé puis rouvert, ou si le retrait automatique est activée, ce qui entraîne le contrôle utilisateur doit être retirée de la ruche SharePoint après le débogage.

 Pour supprimer cet avertissement, générez le projet puis fermez et rouvrez le concepteur, ou désactivez l'option de retrait automatique pour le projet. Pour ce faire, désactivez le **retrait automatique après le débogage** case à cocher sur la **SharePoint** onglet de la boîte de dialogue des propriétés de projet.

## <a name="see-also"></a>Voir aussi

- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)