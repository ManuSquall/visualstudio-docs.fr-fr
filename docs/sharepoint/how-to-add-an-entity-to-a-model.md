---
title: 'Procédure : Ajouter une entité à un modèle | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: b269bb18580784fb08d9b081a37935c7b3f37627
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864658"
---
# <a name="how-to-add-an-entity-to-a-model"></a>Procédure : Ajouter une entité à un modèle
  Pour créer une entité, ajoutez un contrôle de l’entité à partir de Visual Studio **boîte à outils** sur le Concepteur de connectivité de données métiers (BDC).  
  
### <a name="to-add-an-entity-to-the-model"></a>Pour ajouter une entité au modèle  
  
1.  Créer un projet BDC ou ouvrez un projet BDC existant. Pour plus d’informations, consultez [créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
2.  Dans le **boîte à outils**, à partir de la **BusinessDataCatalog** de groupe, ajoutez un **entité** contrôle sur le concepteur.  
  
     La nouvelle entité s’affiche dans le concepteur. Visual Studio ajoute un `<Entity>` élément pour le code XML du fichier de modèle BDC dans votre projet. Pour plus d’informations sur les attributs d’un élément d’entité, consultez [entité](http://go.microsoft.com/fwlink/?LinkId=169296).  
  
3.  Dans le concepteur, ouvrez le menu contextuel de l’entité, choisissez **ajouter**, puis choisissez **identificateur**.  
  
     Un nouvel identificateur s’affiche sur l’entité.  
  
    > [!NOTE]  
    >  Vous pouvez modifier le nom de l’entité et l’identificateur dans le **propriétés** fenêtre.  
  
4.  Définissez les champs de l’entité dans une classe. Vous pouvez ajouter une nouvelle classe au projet ou utiliser une classe existante créée à l’aide d’autres outils tels que le Concepteur Objet/Relationnel (Concepteur O/R). L’exemple suivant montre une classe d’entité nommée Contact.  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]  
  
## <a name="see-also"></a>Voir aussi
 [Guide pratique pour Ajouter une méthode de création](../sharepoint/how-to-add-a-creator-method.md)   
 [Guide pratique pour Ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)   
 [Guide pratique pour Ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)   
 [Guide pratique pour Ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)   
 [Guide pratique pour Ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)  
