---
title: 'Comment : ajouter une zone de formulaire à un projet de complément Outlook'
description: Découvrez comment créer une zone de formulaire pour étendre un formulaire Microsoft Office Outlook standard ou personnalisé à l’aide de l’Assistant Nouvelle zone de formulaire Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VSTO.NewFormRegionWizard.Page1
- VSTO.NewFormRegionWizard.Page3
- VSTO.NewFormRegionWizard.Page2
- VSTO.NewFormRegionWizard.Page0
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9f50475f52ca2ec08894a3c1c0375e78d2b5620b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917536"
---
# <a name="how-to-add-a-form-region-to-an-outlook-add-in-project"></a>Comment : ajouter une zone de formulaire à un projet de complément Outlook
  Créez une zone de formulaire pour étendre un formulaire Microsoft Office Outlook standard ou personnalisé à l’aide de l’Assistant **Nouvelle zone de formulaire Outlook** . Vous pouvez créer une zone de formulaire et concevoir l’interface utilisateur dans Visual Studio, ou vous pouvez importer une zone de formulaire conçue dans Outlook et ajouter du code Visual Basic ou C#.

 Si vous disposez d'une zone de formulaire Outlook que vous avez utilisée dans un autre projet Outlook, vous pouvez la réutiliser dans votre projet de complément VSTO Outlook actuel à l'aide de la boîte de dialogue **Ajouter un élément existant** . Pour plus d’informations, consultez [créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

### <a name="to-add-a-new-form-region-to-an-outlook-project"></a>Pour ajouter une nouvelle zone de formulaire à un projet Outlook

1. Ouvrez ou créez un projet de complément VSTO Outlook dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Dans l’ **Explorateur de solutions**, sélectionnez le nœud de projet de complément Outlook VSTO.

3. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

4. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Zone de formulaire Outlook**.

5. Tapez un nom pour la zone de formulaire dans la zone **Nom** , puis cliquez sur **Ajouter**.

     L’Assistant **zone de formulaire NewOutlook** démarre.

6. Dans la page **Sélectionnez la méthode de création de la zone de formulaire** , indiquez si vous souhaitez concevoir la zone de formulaire en faisant glisser des contrôles managés vers un concepteur visuel ou importer une zone de formulaire conçue dans Outlook.

    > [!NOTE]
    > Si vous choisissez d’importer une zone de formulaire conçue dans Outlook, vous devez spécifier l’emplacement d’un fichier de stockage de formulaire Outlook (*. OFS*). Vous ne pouvez pas ajouter des contrôles managés à une zone de formulaire que vous concevez dans Outlook. Vous pouvez uniquement ajouter du code-behind à l’interface utilisateur existante. Pour plus d’informations, consultez [créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md).

7. Dans la page **Sélectionnez le type de zone de formulaire que vous souhaitez créer** , passez en revue les types de zones de formulaire et sélectionnez-en un, puis cliquez sur **Suivant**. Pour plus d’informations sur les types de zones de formulaire, consultez [créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md).

8. Dans la page **Fournissez un texte descriptif et sélectionnez vos préférences d’affichage** , dans la zone **Nom** , tapez un nom pour la zone de formulaire. Pour les types de zones de formulaire de substitution et de remplacement global, les zones **Titre** et **Description** sont également disponibles.

     Pour plus d’informations sur l’emplacement où le nom, le titre et la description apparaissent dans Outlook lorsque vous déployez la zone de formulaire, consultez [créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md).

9. Sélectionnez un ou plusieurs modes d’affichage dans lesquels vous souhaitez que la zone de formulaire apparaisse.

     Tous les types de zones de formulaire peuvent apparaître dans les inspecteurs, en mode composition (pour créer des éléments) et en mode lecture (pour consulter des éléments). Les types de zones de formulaire adjacents, de substitution et de remplacement global peuvent également apparaître dans le volet de lecture.

10. Cliquez sur **Suivant**.

11. Dans la page **Identifiez les classes de message qui afficheront cette zone de formulaire** , sélectionnez les classes de message Outlook standard ou tapez le nom d’une ou plusieurs classes de message personnalisées, puis cliquez sur **Terminer**. Pour plus d’informations, consultez [associer une zone de formulaire à une classe de message Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

## <a name="see-also"></a>Voir aussi
- [Accéder à une zone de formulaire au moment de l’exécution](../vsto/accessing-a-form-region-at-run-time.md)
- [Solutions Outlook](../vsto/outlook-solutions.md)
- [Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)
- [Instructions pour la création de zones de formulaire Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Procédure pas à pas : conception d’une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Procédure pas à pas : importer une zone de formulaire conçue dans Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Actions personnalisées dans les zones de formulaire Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
