---
title: Instructions pour l’importation de flux de travail réutilisables | Microsoft Docs
description: Passez en revue les instructions pour l’importation de flux de travail réutilisables qui ont été créés dans SharePoint Designer dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aab3d3b73fac086c4ff5aee8b5319a76e9aaea15
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915516"
---
# <a name="guidelines-for-importing-reusable-workflows"></a>Instructions pour l’importation de flux de travail réutilisables
  Pour importer des flux de travail réutilisables créés dans SharePoint Designer, utilisez le modèle de projet importer le flux de travail SharePoint 2010 réutilisable dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Ce modèle importe un *declarative* *flux de travail* déclaratif ( [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] uniquement) et le convertit en un *flux* de travail de code, qui est un flux de travail que vous pouvez améliorer à l’aide de ou du [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] code. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Procédure pas à pas : importation d’un flux de travail réutilisable SharePoint Designer dans Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

 Toutefois, le modèle de flux de travail SharePoint 2010 d’importation réutilisable peut importer uniquement des solutions de batterie de serveurs. Si vous souhaitez déployer votre workflow comme une solution bac à sable (sandbox), importez-le avec le modèle importer le package de solution SharePoint 2010. Toutefois, en procédant ainsi, vous ne pouvez pas le convertir en flux de travail de code et vous ne pourrez pas le modifier en tant que tel.

## <a name="import-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>Importer des flux de travail réutilisables à l’aide du modèle importer le flux de travail réutilisable
 Si vous importez un flux de travail réutilisable à l’aide du modèle d’importation de flux de travail SharePoint 2010 réutilisable, vous pouvez exécuter ou modifier la solution comme n’importe quelle autre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] solution SharePoint, mais vous devrez peut-être corriger manuellement certains éléments.

### <a name="import-task-forms"></a>Importer des formulaires de tâches
 Le modèle de projet importer le flux de travail SharePoint 2010 réutilisable importe tous les formulaires d’initiation et d’association, mais importe un seul formulaire de tâche, car le schéma du flux de travail du code autorise uniquement un formulaire de tâche. Les autres formulaires de tâches de la solution de flux de travail d’origine sont placés dans le dossier **autres fichiers importés** de **Explorateur de solutions**.

## <a name="import-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>Importer des flux de travail réutilisables à l’aide du modèle importer le package de solution SharePoint 2010
 Si vous importez un flux de travail réutilisable à l’aide du modèle importer le package de solution SharePoint 2010, vous devez tenir compte des points suivants :

- Après l’importation du flux de travail, vous pouvez immédiatement le déployer et l’exécuter dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en choisissant la touche **F5** . Toutefois, si vous modifiez quoi que ce soit dans le flux de travail de la solution importée, vous devrez peut-être corriger manuellement les éléments du projet avant de pouvoir déployer et exécuter le Workflow.

- Étant donné que le flux de travail est déclaratif, le code ne peut pas lui être ajouté. Pour convertir le flux de travail en un flux de travail de code, vous devez l’importer dans à [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] l’aide du modèle de flux de travail SharePoint 2010 d’importation réutilisable.

- Bien que vous puissiez modifier le fichier du concepteur de flux de travail (. xoml) dans Mode Création, il est recommandé de le modifier en mode Source, car le concepteur de flux de travail affiche des erreurs erronées.

- Le débogage dans le flux de travail ne fonctionne pas pour le contenu déclaratif. Les points d’arrêt définis dans le ne [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] sont pas atteints.

## <a name="import-globally-reusable-workflow-solutions"></a>Importer des solutions de flux de travail réutilisables globalement
 Les flux de travail réutilisables globalement ne peuvent pas être importés à l’aide du modèle de flux de travail SharePoint 2010 réutilisable pour l’importation. Pour importer un flux de travail globalement réutilisable, vous devez le convertir en un flux de travail non réutilisable globalement, ou vous devez utiliser le modèle importer le package de solution SharePoint 2010.

 Pour convertir le flux de travail, effectuez une copie du flux de travail globalement réutilisable dans SharePoint Designer (en ouvrant le menu contextuel du flux de travail, puis en choisissant **Enregistrer comme copie**). Importez ensuite le nouveau flux de travail réutilisable avec le modèle importer le flux de travail SharePoint 2010 réutilisable dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 Pour importer le flux de travail réutilisable globalement sans le modifier, utilisez le modèle importer le package de solution SharePoint 2010. Si vous utilisez cette méthode, le flux de travail n’est pas converti en flux de travail de code et reste un flux de travail déclaratif.

## <a name="see-also"></a>Voir aussi
- [Importer des éléments à partir d’un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Procédure pas à pas : importer un flux de travail réutilisable SharePoint Designer dans Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
