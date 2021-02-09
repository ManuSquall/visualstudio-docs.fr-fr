---
title: 'Comment : ajouter un fichier de modèle BDC existant à un projet SharePoint | Microsoft Docs'
titleSuffix: ''
description: Ajoutez un fichier de modèle de connectivité de données métiers (BDC) existant à un projet SharePoint dans Visual Studio, afin de pouvoir personnaliser, empaqueter et redéployer un modèle BDC.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: af0768b4834eb1cad3654b6d74ee8f02cf464245
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882672"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Comment : ajouter un fichier de modèle BDC existant à un projet SharePoint
  Vous pouvez personnaliser, empaqueter et redéployer un modèle de connectivité de données métiers (BDC) à l’aide de Visual Studio pour ajouter le fichier de modèle (*. BDCM*) à n’importe quel projet de batterie de serveurs SharePoint. Pour plus d’informations, consultez [créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).

### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Pour ajouter un fichier de modèle BDC à un projet SharePoint

1. Dans **Explorateur de solutions**, choisissez le dossier d’un projet SharePoint.

2. Dans la barre de menus, choisissez **projet**  >  **Ajouter un élément existant**.

3. Dans la boîte de dialogue **Ajouter un élément existant** , accédez à l’emplacement du fichier de définition de modèle que vous souhaitez ajouter à votre projet, sélectionnez le fichier, puis cliquez sur le bouton **Ajouter** .

    Si le modèle ne définit pas un *système métier de type assembly .net*, la boîte de dialogue **Ajouter un LobSystem d’assembly .net** s’ouvre.

4. Si la boîte de dialogue s’affiche, effectuez l’une des opérations suivantes :

   - Si vous souhaitez écrire du code personnalisé et utiliser un concepteur pour définir les métadonnées du modèle importé, choisissez le bouton **Oui** , nommez le système, puis choisissez le bouton **OK** .

   - Dans le cas contraire, choisissez le bouton **non** , puis choisissez le bouton **OK** .

     L’élément de **modèle de connectivité de données métiers** est ajouté au projet.

## <a name="see-also"></a>Voir aussi
- [Créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Comment : créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Comment : utiliser un fichier de ressources pour spécifier des noms localisés, des propriétés et des autorisations](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Comment : inclure un assembly personnalisé dans une fonctionnalité BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
