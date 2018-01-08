---
title: "Comment : créer un modèle BDC | Documents Microsoft"
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
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
ms.assetid: e8b888d4-a531-4d13-9ebf-efbbd33eebc6
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: fb9cab573243882fb0bd410d69941b01ae290994
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-bdc-model"></a>Comment : créer un modèle BDC
  Vous pouvez créer un modèle de connectivité de données métiers (BDC) en utilisant le modèle pour ce type d’élément, puis ajouter le modèle à un projet SharePoint. Pour plus d’informations, consultez [création d’un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md). Pour plus d’informations sur la façon de concevoir le modèle, consultez [vous concevez un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-bdc-project"></a>Pour créer un projet BDC  
  
1.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
    > [!NOTE]  
    >  Si votre interface IDE est définie pour utiliser les paramètres de développement Visual Basic, choisissez **fichier**, **nouveau projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
2.  Sous **Visual Basic** ou **Visual C#**, choisissez **Office/SharePoint**, **Solutions SharePoint**.  
  
3.  Dans le **modèles** volet, choisissez la **SharePoint 2013 - projet vide** d’élément, puis choisissez le **OK** bouton.  
  
     Le **Assistant Personnalisation de SharePoint** s’ouvre.  
  
4.  Sur le **spécifier le niveau de site et de sécurité pour le débogage** page, spécifiez l’URL d’un site SharePoint sur l’ordinateur local, sélectionnez le **déployer en tant que solution de batterie** case d’option, puis choisissez le **Terminer** bouton.  
  
     Vous allez tester le modèle sur le site SharePoint que vous avez spécifié.  
  
    > [!IMPORTANT]  
    >  Étant donné que les modèles BDC prend en charge uniquement des solutions de batterie de serveurs, vous devez déployer le projet comme une solution de batterie de serveurs.  
  
     Un projet SharePoint vide est créé.  
  
5.  Dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément**.  
  
6.  Dans le **ajouter un nouvel élément** boîte de dialogue, choisissez le **Office/SharePoint** nœud.  
  
7.  Dans la liste de modèles SharePoint, choisissez **modèle de connectivité de données métiers (Solution de batterie uniquement)**.  
  
8.  Dans le **nom** zone, spécifiez un nom pour le modèle BDC, puis choisissez le **ajouter** bouton.  
  
     A **modèle de connectivité de données métiers** élément est ajouté au projet. Par défaut, le modèle apparaît dans le concepteur BDC. Pour plus d’informations, consultez [création d’un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Comment : ajouter un fichier de modèle BDC existant à un projet SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Comment : utiliser un fichier de ressources pour spécifier des noms localisés, propriétés et autorisations](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Comment : inclure un Assembly personnalisé dans une fonctionnalité BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  