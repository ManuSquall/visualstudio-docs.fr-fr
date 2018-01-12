---
title: "Résolution des problèmes d’empaquetage de SharePoint et de déploiement | Documents Microsoft"
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a2c9cbb7b0b9e7f0536fb393bcea3d0873e0d90a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="troubleshooting-sharepoint-packaging-and-deployment"></a>Dépannage de la création de packages et du déploiement SharePoint
  Cette rubrique couvre différents problèmes que vous pouvez rencontrer lorsque vous empaquetez et déployez des solutions SharePoint.  
  
## <a name="enabling-enhanced-debugging"></a>Activation du débogage avancé  
 Pour effectuer un diagnostic entre Visual Studio, SharePoint et d'autres couches, vous pouvez utiliser la clé de Registre EnableDiagnostics afin de consulter la trace de la pile. Pour plus d’informations, consultez [débogage de Solutions SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
## <a name="adding-project-output-to-the-solution-package"></a>Ajout de la sortie de projet au package de solution  
 Vous pouvez ajouter la sortie de projet à un package via le Concepteur de packages. Toutefois, lorsque vous ajoutez la sortie de projet, assurez-vous que la plateforme du projet correspond à la plateforme de la solution SharePoint. Nous vous recommandons d’utiliser le **Any CPU** plateforme cible pour les assemblys que vous souhaitez déployer sur un serveur SharePoint. Pour plus d’informations, consultez [Page Compiler, Concepteur de projets &#40; Visual Basic &#41; ](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) et [avancé de boîte de dialogue Paramètres du compilateur &#40; Visual Basic &#41; ](/visualstudio/ide/reference/advanced-compiler-settings-dialog-box-visual-basic).  
  
## <a name="validation-warnings-and-errors"></a>Erreurs et avertissements de validation  
 Les outils de développement SharePoint dans Visual Studio exécutent des étapes de validation pour vérifier que le package de solution est correctement formé. Vous pouvez également créer des étapes de validation personnalisées pour vos fonctionnalités et vos packages. Pour plus d’informations, consultez [Comment : créer des fonctionnalités personnalisées et les règles de Validation de Package pour les Solutions SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
## <a name="deployment-conflict-resolution"></a>Résolution de conflit de déploiement  
 Lorsque vous déployez une solution SharePoint, vous pouvez être confronté à des collisions lorsqu'un élément sur le serveur a un nom, une URL ou un ID identique à celui ou celle d'un élément dans votre package de solution. Vous pouvez modifier le **Deployment Conflict Resolution** propriété à résoudre, signaler ou ignorer des collisions relatives des modules, les parties Web, les instances de listes et les types de contenu.  
  
 Le tableau suivant montre les paramètres pour le **Deployment Conflict Resolution** propriété.  
  
|Value|Description|  
|-----------|-----------------|  
|Automatique|Détecte les collisions et résout automatiquement les conflits.|  
|Invite|Détecte les collisions et les signale au développeur avant de résoudre les conflits.|  
|Aucun.|Ne détecte pas les collisions.|  
  
## <a name="differences-between-f5-deployment"></a>Différences entre le déploiement F5  
 Lorsque vous utilisez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pour déployer votre projet SharePoint sur le serveur SharePoint local à des fins de test et de débogage, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] exécute des opérations supplémentaires.  
  
1.  Réinitialisation des services IIS (Internet Information Services) pendant l'étape de déploiement.  
  
2.  Association automatique des flux de travail.  
  
3.  Définition de l’ordre d’activation des fonctionnalités en fonction de la hiérarchie du Concepteur de packages.  
  
 Vous pouvez ajouter des étapes de déploiement personnalisées pour modifier davantage le comportement F5. Pour plus d’informations, consultez [procédure pas à pas : création d’une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## <a name="delay-displaying-sharepoint-page-when-deploying-visual-web-part"></a>Différer l'affichage de la page SharePoint lors du déploiement d'un composant Visual Web Part  
 L'affichage de la page SharePoint prend un certain temps lors du déploiement d'un composant Visual Web Part dans le dossier Bin sur [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)], [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] ou [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]. Si vous modifiez des fichiers dans un répertoire [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] de niveau supérieur, tel que le répertoire bin, l'application Web entière est recompilée. Cela peut différer de 25 secondes le rendu de la page SharePoint.  
  
### <a name="error-message"></a>Message d'erreur  
 Aucun.  
  
### <a name="resolution"></a>Résolution  
 Pour contourner ce problème, exécutez les étapes suivantes :  
  
1.  Installer la mise à jour KB967535 comme indiqué dans l’article du Support technique de Microsoft [FIX : un correctif est disponible pour résoudre les deux problèmes dans ASP.NET sur IIS 7.0 pour Windows Vista et Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=179055).  
  
2.  Ajoutez la ligne suivante au fichier Web.config :  
  
    ```  
    <compilation batch="false" optimizeCompilations="true">  
    ```  
  
## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>Le déploiement du projet SharePoint échoue avec l'erreur « Échec de l'extraction du fichier .cab dans la solution »  
 Si le nom d'un élément de projet SharePoint quelconque contient des parenthèses, le déploiement de la solution associée échoue avec une erreur.  
  
### <a name="error-message"></a>Message d'erreur  
 Une erreur s'est produite lors de l'étape de déploiement 'Ajouter une solution' : Échec de l'extraction du fichier .cab dans la solution.  
  
### <a name="resolution"></a>Résolution  
 Pour résoudre ce problème, supprimez les parenthèses dans les noms d'éléments de projet SharePoint.  
  
## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>Une erreur survient lors du déploiement d'un élément Visual Web Part sur un site d'une autre application Web  
 La première fois que vous déployez un élément Visual Web Part sur un site d'une application Web autre que celle dans laquelle il est actuellement déployé (en modifiant la propriété SiteUrl de l'élément Visual Web Part), vous obtenez une erreur.  
  
### <a name="error-message"></a>Message d'erreur  
 Une erreur s'est produite lors de l'étape de déploiement 'Ajouter une solution' : Une fonctionnalité avec l'ID [#] a déjà été installée dans cette batterie de serveur. Utilisez l’attribut force pour installer à nouveau la fonctionnalité de façon explicite.  
  
### <a name="resolution"></a>Résolution  
 Cette erreur est due au mode de retrait des fonctionnalités d'éléments Visual Web Part dans SharePoint. Pour déployer correctement le composant Visual Web Part, déployez de nouveau la solution en choisissant la touche F5.  
  
## <a name="warning-appears-when-deploying-nested-user-controls"></a>Un avertissement s'affiche lors du déploiement de contrôles utilisateur imbriqués  
 Cet avertissement se produit lorsque vous déployez une solution SharePoint qui contient des contrôles utilisateur imbriqués, tels qu'un composant Visual Web Part qui contient un contrôle utilisateur ou un contrôle utilisateur qui contient un composant Visual Web Part ou un autre contrôle utilisateur. Cet avertissement se produit si vous ajoutez un contrôle à un concepteur en le faisant glisser à partir de la boîte à outils ou en utilisant la @Register directive dans la vue de Source.  
  
### <a name="error-message"></a>Message d'erreur  
 Avertissement 1 l’élément ' [*nom du contrôle*]' n’est pas un élément connu. Ceci peut se produire s’il existe une erreur de compilation dans le site web ou si le fichier Web.config est manquant.  
  
### <a name="resolution"></a>Résolution  
 Si le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] système de projet n’a pas connaissance d’un contrôle utilisateur imbriqué, il ne peut pas fournir Intellisense et il émet l’avertissement. Le système de projet n’a pas connaissance d’un contrôle utilisateur imbriqué si le projet n’est pas généré et le concepteur n’est pas fermé et rouvert, ou si le retrait automatique est activée, ce qui entraîne le contrôle utilisateur doit être retirée de la ruche SharePoint après le débogage.  
  
 Pour supprimer cet avertissement, générez le projet puis fermez et rouvrez le concepteur, ou désactivez l'option de retrait automatique pour le projet. Pour ce faire, désactivez le **retrait automatique après le débogage** case à cocher sur la **SharePoint** onglet de la boîte de dialogue Propriétés du projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  
