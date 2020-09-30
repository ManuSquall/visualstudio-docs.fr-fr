---
title: Comment utiliser un fichier de ressources dans un projet SharePoint | Microsoft Docs
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1693308c591e60a2df0e4d8e18ece8cc9b598fd2
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585743"
---
# <a name="how-to-use-a-resource-file-in-a-sharepoint-project"></a>Comment utiliser un fichier de ressources dans un projet SharePoint

  À l’aide d’un fichier de ressources, vous pouvez fournir des noms localisés, définir des propriétés et appliquer des autorisations correspondant aux objets définis dans un modèle de connectivité de données métiers (BDC). Pour spécifier ces informations, vous ajoutez un élément de **ressource de connectivité de données métiers** à un projet qui contient un élément de **modèle de connectivité de données métiers** . Ensuite, vous spécifiez des noms, des propriétés et des autorisations en modifiant le XML pour le fichier de ressources.

### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Pour ajouter un fichier de ressources BDC à un projet SharePoint

1. Dans **Explorateur de solutions**, développez le dossier du projet SharePoint, puis choisissez le dossier qui contient le modèle BDC.

2. Dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**.

3. Développez le nœud **SharePoint** , puis choisissez le nœud **2010** .

4. Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez **élément de ressource connectivité de données métiers**.

5. Dans la zone **nom** , spécifiez le nom du fichier de ressources, puis choisissez le bouton **Ajouter** .

     Un fichier de ressources avec l’extension. bdcr est ajouté au projet et ouvert pour modification.

6. Ajoutez XML pour définir les noms localisés, les propriétés et les autorisations que vous souhaitez appliquer au modèle BDC.

     Pour plus d’informations sur la définition de ces éléments, consultez [fichiers de modèle et de ressources](/previous-versions/office/developer/sharepoint-2010/aa674515(v=office.14)).

## <a name="see-also"></a>Voir aussi
- [Comment : ajouter un fichier de modèle BDC existant à un projet SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Comment : créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Comment : inclure un assembly personnalisé dans une fonctionnalité BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
