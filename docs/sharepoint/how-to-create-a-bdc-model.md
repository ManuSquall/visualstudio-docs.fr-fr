---
title: 'Procédure : Créer un modèle BDC | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4d0d261b0227e024b5b4eda89b237df0c70dbd32
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870046"
---
# <a name="how-to-create-a-bdc-model"></a>Procédure : Créer un modèle BDC
  Vous pouvez créer un modèle de connectivité de données métiers (BDC) en utilisant le modèle pour ce type d’élément, puis ajouter le modèle à un projet SharePoint. Pour plus d’informations, consultez [créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md). Pour plus d’informations sur la façon de concevoir le modèle, consultez [concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-bdc-project"></a>Pour créer un projet BDC  
  
1.  Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**.  
  
    > [!NOTE]  
    >  Si votre interface IDE est définie pour utiliser les paramètres de développement Visual Basic, choisissez **fichier** > **nouveau projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
2.  Sous **Visual Basic** ou **Visual C#**, choisissez **Office/SharePoint**, **Solutions SharePoint**.  
  
3.  Dans le **modèles** volet, choisissez le **SharePoint 2013 - projet vide** d’élément, puis choisissez le **OK** bouton.  
  
     Le **Assistant Personnalisation de SharePoint** s’ouvre.  
  
4.  Sur le **spécifier le niveau de site et de sécurité pour le débogage** page, spécifiez l’URL d’un site SharePoint sur l’ordinateur local, choisissez le **déployer en tant que solution de batterie** case d’option, puis choisissez le **Terminer** bouton.  
  
     Vous allez tester le modèle sur le site SharePoint que vous avez spécifié.  
  
    > [!IMPORTANT]  
    >  Étant donné que les modèles BDC prennent en charge uniquement les solutions de batterie de serveurs, vous devez déployer le projet comme une solution de batterie de serveurs.  
  
     Un projet SharePoint vide est créé.  
  
5.  Dans la barre de menus, choisissez **Projet** > **Ajouter un nouvel élément**.  
  
6.  Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez le **Office/SharePoint** nœud.  
  
7.  Dans la liste de modèles SharePoint, choisissez **modèle de connectivité de données métiers (Solution de batterie uniquement)**.  
  
8.  Dans le **nom** zone, spécifiez un nom pour le modèle BDC, puis choisissez le **ajouter** bouton.  
  
     Un **modèle de connectivité de données métiers** élément est ajouté au projet. Par défaut, le modèle apparaît dans le concepteur BDC. Pour plus d’informations, consultez [créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="see-also"></a>Voir aussi
 [Créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Guide pratique pour Ajouter un fichier de modèle BDC existant à un projet SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Guide pratique pour Utilisez un fichier de ressources pour spécifier des autorisations, les propriétés et les noms localisés](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Guide pratique pour Inclure un assembly personnalisé dans une fonctionnalité BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
