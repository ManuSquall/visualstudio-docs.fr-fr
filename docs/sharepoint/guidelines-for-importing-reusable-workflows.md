---
title: "Directives pour l’importation de flux de travail réutilisables | Documents Microsoft"
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
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
ms.assetid: 851043dd-ecbe-49ab-b5b7-5ea7b699df12
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9f0ba8bdd5e599fadc98519d54a3015abf91f013
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="guidelines-for-importing-reusable-workflows"></a>Directives pour l'importation de flux de travail réutilisables
  Pour importer des flux de travail réutilisables créés dans SharePoint Designer, utilisez le modèle de projet importer SharePoint 2010 flux de travail réutilisable dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Ce modèle importe un *déclarative* *workflow* ([!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-uniquement) et le convertit en un *du flux de travail de code*, qui est un flux de travail pouvant être amélioré avec [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] code. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Procédure pas à pas : importation d’un flux de travail réutilisable de SharePoint Designer dans Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
 Toutefois, le modèle Importer SharePoint 2010 réutilisable peut importer uniquement des solutions de batterie de serveurs. Si vous souhaitez déployer votre flux de travail comme une solution bac à sable, importez-le avec le modèle Importer le Package de Solution SharePoint 2010. Toutefois, ce faisant, vous ne peut pas convertir pour coder des flux de travail et ne sera pas en mesure de le modifier en tant que tel.  
  
## <a name="importing-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>L’importation de flux de travail réutilisables en utilisant le modèle de flux de travail réutilisable d’importation  
 Si vous importez un flux de travail réutilisable à l’aide du modèle Importer SharePoint 2010 flux de travail réutilisable, vous pouvez exécuter ou modifier la solution comme toute autre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] solution SharePoint, mais vous devrez peut-être corriger manuellement certains éléments.  
  
### <a name="importing-task-forms"></a>L’importation des formulaires de tâches  
 Le modèle de projet d’importation de flux de travail réutilisable SharePoint 2010 importe tous les formulaires d’initiation et d’association, mais les importations d’une seule tâche, car le schéma de flux de travail de code ne permet qu’un formulaire de tâche. Les formulaires de tâches supplémentaires à partir de la solution de flux de travail d’origine sont placés dans le **autres fichiers importés** dossier **l’Explorateur de solutions**.  
  
## <a name="importing-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>L’importation de flux de travail réutilisables à l’aide du modèle de Package de Solution 2010 SharePoint importation  
 Si vous importez un flux de travail réutilisable à l’aide du modèle Importer le Package de Solution SharePoint 2010, vous devez envisager les problèmes suivants :  
  
-   Après avoir importé le flux de travail, vous pouvez immédiatement déployer et exécuter dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en choisissant la touche F5. Toutefois, si vous modifiez n’importe où dans le flux de travail dans la solution importée, vous devrez résoudre manuellement des éléments dans le projet avant de pouvoir déployer et exécuter le flux de travail.  
  
-   Étant donné que le flux de travail est déclaratif, code ne peut pas être ajouté. Pour convertir le flux de travail dans un workflow de code, vous devez l’importer dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en utilisant le modèle Importer SharePoint 2010 réutilisable.  
  
-   Pendant que vous pouvez modifier le fichier de concepteur (.xoml) de flux de travail en mode conception, il est recommandé de modifier en mode Source, car le Concepteur de workflow affiche des erreurs.  
  
-   Débogage dans le flux de travail ne fonctionne pas pour le contenu déclaratif. Points d’arrêt définis le [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] ne sont pas atteints.  
  
## <a name="importing-globally-reusable-workflow-solutions"></a>L’importation de Solutions de flux de travail réutilisable globalement  
 Impossible d’importer des flux de travail globalement réutilisables en utilisant le modèle d’importation réutilisable SharePoint 2010 Workflow. Pour importer un flux de travail réutilisable globalement, vous devez le convertir en un flux de travail réutilisable non globalement ou vous devez utiliser le modèle Importer le Package de Solution SharePoint 2010.  
  
 Pour convertir le flux de travail, effectuez une copie du flux de travail globalement réutilisable dans SharePoint Designer (en ouvrant le menu contextuel pour le flux de travail, puis en choisissant **enregistrer en tant que copie**). Puis importer le nouveau flux de travail réutilisable avec le modèle Importer SharePoint 2010 flux de travail réutilisable dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Pour importer le flux de travail réutilisable globalement sans le modifier, utilisez le modèle Importer le Package de Solution SharePoint 2010. Si vous utilisez cette méthode, le flux de travail n’est pas converti en un flux de travail de code et reste un flux de travail déclaratif.  
  
## <a name="see-also"></a>Voir aussi  
 [Importation d’éléments d’un Site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Procédure pas à pas : importation d’un flux de travail réutilisable de SharePoint Designer dans Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)  
  
  