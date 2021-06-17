---
title: 'Comment : créer un modèle BDC | Microsoft Docs'
description: Créez un modèle de connectivité de données métiers (BDC) à l’aide du modèle Visual Studio pour ce type d’élément, puis ajoutez le modèle à n’importe quel projet SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fd5184f87cf3895e1519a91e6f7e6661702f1181
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112412"
---
# <a name="how-to-create-a-bdc-model"></a>Comment : créer un modèle BDC

  Vous pouvez créer un modèle de connectivité de données métiers (BDC) à l’aide du modèle pour ce type d’élément, puis ajouter le modèle à n’importe quel projet SharePoint. Pour plus d’informations, consultez [créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md). Pour plus d’informations sur la conception du modèle, consultez [concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).

## <a name="to-create-a-bdc-project"></a>Pour créer un projet BDC

1. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**.
::: moniker range="=vs-2017"
   > [!NOTE]
   > Si votre IDE est configuré pour utiliser Visual Basic paramètres de développement, choisissez **fichier**  >  **nouveau projet**.

  La boîte de dialogue **Nouveau projet** s’affiche.

2. Sous **Visual Basic** ou **Visual C#**, choisissez **Office/SharePoint**, **solutions SharePoint**.

3. Dans le volet **modèles** , choisissez l’élément de **projet SharePoint 2013-vide** , puis cliquez sur le bouton **OK** .

     L' **Assistant Personnalisation de SharePoint** s’ouvre.
::: moniker-end
::: moniker range=">=vs-2019"
2. Dans la boîte de dialogue **créer un nouveau projet** , sélectionnez le *projet vide SharePoint** pour la version particulière de SharePoint que vous avez installée. Par exemple, si vous avez SharePoint 2019 installer, sélectionnez le modèle **de projet sharepoint 2019-vide** .
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Modifiez le nom du projet si vous le souhaitez, puis choisissez le bouton **créer** .

::: moniker-end
4. Dans la page **spécifier le site et le niveau de sécurité pour le débogage** , spécifiez l’URL d’un site SharePoint sur l’ordinateur local, sélectionnez la case d’option **déployer en tant que solution de batterie** , puis choisissez le bouton **Terminer** .

     Vous allez tester le modèle sur le site SharePoint que vous avez spécifié.

    > [!IMPORTANT]
    > Vous devez déployer le projet en tant que solution de batterie de serveurs, car les modèles BDC ne prennent en charge que les solutions de batterie.

     Un projet SharePoint vide est créé.

5. Dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**.

6. Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez le nœud **Office/SharePoint** .

7. Dans la liste des modèles SharePoint, choisissez **modèle de connectivité de données métiers (solution de batterie uniquement)**.

8. Dans la zone **nom** , spécifiez un nom pour le modèle BDC, puis cliquez sur le bouton **Ajouter** .

     Un élément de **modèle de connectivité de données métiers** est ajouté au projet. Par défaut, le modèle s’affiche dans le concepteur BDC. Pour plus d’informations, consultez [créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="see-also"></a>Voir aussi

- [Créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Comment : ajouter un fichier de modèle BDC existant à un projet SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Comment : utiliser un fichier de ressources pour spécifier des noms localisés, des propriétés et des autorisations](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Comment : inclure un assembly personnalisé dans une fonctionnalité BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
