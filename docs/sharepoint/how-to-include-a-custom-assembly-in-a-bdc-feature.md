---
title: 'Comment : inclure un assembly personnalisé dans une fonctionnalité BDC | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 772cdbaca67cc82fc6b7eb2c5ef5adb6508df34a
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015257"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Comment : inclure un assembly personnalisé dans une fonctionnalité BDC
  Votre projet peut référencer des assemblys d’autres projets dans la même solution. Toutefois, vous devez ajouter ces assemblys au fichier de fonctionnalité du projet à l’aide de la boîte de dialogue **assigner les assemblys référencés aux LobSystems** .

### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Pour inclure un assembly personnalisé dans une fonctionnalité de connectivité de données métiers (BDC)

1. Dans **Explorateur de solutions**, choisissez le dossier qui contient le modèle BDC.

2. Dans le menu **Affichage** , cliquez sur **Fenêtre Propriétés**.

3. Dans la fenêtre **Propriétés** , choisissez la propriété **assemblys** , puis le bouton de sélection (![ellipse ASP.net Mobile designer](../sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile")).

     La boîte **de dialogue assigner les assemblys référencés aux LobSystems** s’affiche.

4. Dans la liste **Sélectionner un assembly** , choisissez l’assembly personnalisé.

    > [!NOTE]
    > Les assemblys apparaissent uniquement dans la boîte de dialogue **assigner des assemblys référencés aux LobSystems** si vous avez ajouté une référence au projet qui contient l’assembly. Pour plus d’informations, consultez [Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

5. Dans le groupe **Propriétés de référence** , ouvrez la liste qui s’affiche pour la propriété **étendue LobSystem** , choisissez le système LOB des méthodes qui utilisent l’assembly personnalisé, puis cliquez sur le bouton **OK** .

    > [!NOTE]
    > Pour déboguer du code dans l’assembly personnalisé, vous devez ajouter l’assembly au package de solution. Pour plus d’informations, consultez [Comment : ajouter et supprimer des assemblys supplémentaires](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

## <a name="see-also"></a>Voir aussi
- [Comment : utiliser un fichier de ressources pour spécifier des noms localisés, des propriétés et des autorisations](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Comment : ajouter un fichier de modèle BDC existant à un projet SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Comment : créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Integragte des données d’entreprise dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
