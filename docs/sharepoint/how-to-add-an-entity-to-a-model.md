---
title: 'Comment : ajouter une entité à un modèle | Microsoft Docs'
description: Ajoutez une entité à un modèle en ajoutant un contrôle d’entité à partir de la boîte à outils Visual Studio sur le concepteur de connectivité de données métiers (BDC).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- EntityTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0efd7a6fc0d6254dbfd3cbda538ffe0e30585453
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915386"
---
# <a name="how-to-add-an-entity-to-a-model"></a>Comment : ajouter une entité à un modèle
  Pour créer une entité, ajoutez un contrôle d’entité à partir de la **boîte à outils** Visual Studio sur le concepteur de connectivité de données métiers (BDC).

### <a name="to-add-an-entity-to-the-model"></a>Pour ajouter une entité au modèle

1. Créez un projet BDC ou ouvrez un projet BDC existant. Pour plus d’informations, consultez [créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).

2. Dans la **boîte à outils**, à partir du groupe **BusinessDataCatalog** , ajoutez un contrôle d' **entité** sur le concepteur.

     La nouvelle entité s’affiche sur le concepteur. Visual Studio ajoute un `<Entity>` élément au XML du fichier de modèle BDC dans votre projet. Pour plus d’informations sur les attributs d’un élément d’entité, consultez [entité](/previous-versions/office/developer/sharepoint-2010/ee558325(v=office.14)).

3. Dans le concepteur, ouvrez le menu contextuel de l’entité, choisissez **Ajouter**, puis **identificateur**.

     Un nouvel identificateur apparaît sur l’entité.

    > [!NOTE]
    > Vous pouvez modifier le nom de l’entité et l’identificateur dans la fenêtre **Propriétés** .

4. Définissez les champs de l’entité dans une classe. Vous pouvez ajouter une nouvelle classe au projet ou utiliser une classe existante créée à l’aide d’autres outils tels que le Concepteur Objet Relationnel (Concepteur O/R). L’exemple suivant montre une classe d’entité nommée contact.

     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]

## <a name="see-also"></a>Voir aussi
- [Comment : ajouter une méthode Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Comment : ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)
- [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)
- [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)
- [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)
