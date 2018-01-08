---
title: "Comment : ajouter un fichier de modèle BDC existant à un projet SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
ms.assetid: e843738a-f936-4dcd-be35-249407573b74
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 64a32115aa7810352148a61e3dd0faeebb0ee9a1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Comment : ajouter un fichier de modèle BDC existant à un projet SharePoint
  Vous pouvez personnaliser, empaqueter et redéployer un modèle de connectivité de données métiers (BDC) à l’aide de Visual Studio pour ajouter le fichier de modèle (.bdcm) à un projet de la batterie de serveurs SharePoint. Pour plus d’informations, consultez [création d’un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Pour ajouter un fichier de modèle BDC à un projet SharePoint  
  
1.  Dans **l’Explorateur de solutions**, choisissez le dossier pour un projet SharePoint.  
  
2.  Dans la barre de menus, choisissez **projet**, **ajouter un élément existant**.  
  
3.  Dans le **ajouter un élément existant** boîte de dialogue, accédez à l’emplacement du fichier de définition de modèle que vous souhaitez ajouter à votre projet, choisissez le fichier, puis le **ajouter** bouton.  
  
     Si le modèle ne définit pas un *système métier (LOB) de type assembly .NET*, le **ajouter un assembly .NET LobSystem** boîte de dialogue s’ouvre.  
  
4.  Si la boîte de dialogue s’affiche, effectuez l’une des étapes suivantes :  
  
    -   Si vous souhaitez écrire du code personnalisé et utiliser un concepteur pour définir les métadonnées du modèle importé, choisissez le **Oui** bouton, nommez le système, puis choisissez le **OK** bouton.  
  
    -   Sinon, choisissez le **non** bouton, puis choisissez le **OK** bouton.  
  
     Le **modèle de connectivité de données métiers** élément est ajouté au projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Comment : créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Comment : utiliser un fichier de ressources pour spécifier des noms localisés, propriétés et autorisations](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Comment : inclure un Assembly personnalisé dans une fonctionnalité BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  