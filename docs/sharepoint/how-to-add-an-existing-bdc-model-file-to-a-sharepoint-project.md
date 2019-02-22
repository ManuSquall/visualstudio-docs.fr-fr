---
title: 'Procédure : Ajouter un fichier de modèle BDC existant à un projet SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9c10dcf48e5c047778b86c524b35b4e1d5d8cc8a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614621"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Procédure : Ajouter un fichier de modèle BDC existant à un projet SharePoint
  Vous pouvez personnaliser, empaqueter et redéployer un modèle de connectivité de données métiers (BDC) à l’aide de Visual Studio pour ajouter le fichier de modèle (*.bdcm*) à un projet de la batterie de serveurs SharePoint. Pour plus d’informations, consultez [créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).

### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Pour ajouter un fichier de modèle BDC à un projet SharePoint

1. Dans **l’Explorateur de solutions**, choisissez le dossier d’un projet SharePoint.

2. Dans la barre de menus, choisissez **projet** > **ajouter un élément existant**.

3. Dans le **ajouter un élément existant** boîte de dialogue, accédez à l’emplacement du fichier de définition de modèle que vous souhaitez ajouter à votre projet, choisissez le fichier, puis le **ajouter** bouton.

    Si le modèle ne définit pas un *système métier (LOB) de type assembly .NET*, le **LobSystem d’assembly .NET ajouter** boîte de dialogue s’ouvre.

4. Si la boîte de dialogue s’affiche, effectuez l’une des étapes suivantes :

   - Si vous souhaitez écrire du code personnalisé et utiliser un concepteur pour définir les métadonnées du modèle importé, choisissez le **Oui** bouton, nommez le système, puis choisissez le **OK** bouton.

   - Sinon, choisissez le **non** bouton, puis choisissez le **OK** bouton.

     Le **modèle de connectivité de données métiers** élément est ajouté au projet.

## <a name="see-also"></a>Voir aussi
- [Créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Guide pratique pour Créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Guide pratique pour Utilisez un fichier de ressources pour spécifier des autorisations, les propriétés et les noms localisés](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Guide pratique pour Inclure un assembly personnalisé dans une fonctionnalité BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
