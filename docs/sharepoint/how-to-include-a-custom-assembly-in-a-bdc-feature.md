---
title: 'Procédure : Inclure un Assembly personnalisé dans une fonctionnalité BDC | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: efbbef540ddd7759fe0614eecccc663368bd23b8
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633614"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Procédure : Inclure un assembly personnalisé dans une fonctionnalité BDC
  Votre projet peut référencer des assemblys à partir d’autres projets dans la même solution. Toutefois, vous devez ajouter ces assemblys dans le fichier de fonctionnalité du projet à l’aide de la **affecter les assemblys à des LobSystems référencés** boîte de dialogue.

### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Pour inclure un assembly personnalisé dans une fonctionnalité de connectivité (BDC) de données métier

1.  Dans **l’Explorateur de solutions**, choisissez le dossier qui contient le modèle BDC.

2.  Dans le menu **Affichage** , cliquez sur **Fenêtre Propriétés**.

3.  Dans le **propriétés** fenêtre, choisissez le **assemblys** propriété, puis sur le bouton de sélection (![ellipse de concepteur ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Ellipse de concepteur")).

     Le **affecter les assemblys à des LobSystems référencés** boîte de dialogue s’affiche.

4.  Dans le **sélectionner un Assembly** , sélectionnez l’assembly personnalisé.

    > [!NOTE]
    >  Assemblys s’affichent uniquement dans le **affecter les assemblys à des LobSystems référencés** boîte de dialogue si vous avez ajouté une référence au projet qui contient l’assembly. Pour plus d'informations, voir [Procédure : Ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter référence](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

5.  Dans le **propriétés de la référence** de groupe, ouvrez la liste qui s’affiche pour le **portée de LobSystem** propriété, choisissez le système LOB des méthodes qui utilisent l’assembly personnalisé, puis choisissez le **OK**  bouton.

    > [!NOTE]
    >  Pour déboguer le code dans l’assembly personnalisé, vous devez ajouter l’assembly pour le package de solution. Pour plus d'informations, voir [Procédure : Ajouter et supprimer des assemblys supplémentaires](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Utilisez un fichier de ressources pour spécifier des autorisations, les propriétés et les noms localisés](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Guide pratique pour Ajouter un fichier de modèle BDC existant à un projet SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Guide pratique pour Créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Données d’entreprise Integragte dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
