---
title: 'Comment : créer un récepteur d’événements pour une instance de liste spécifique | Microsoft Docs'
titleSuffix: ''
description: Créer un récepteur d’événements pour une instance de liste spécifique. Un récepteur d’événements de l’instance de liste répond aux événements qui se produisent dans une instance d’une définition de liste.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 664a7ac4e763b2378cf30603c417aacde27c2e47
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925489"
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>Comment : créer un récepteur d’événements pour une instance de liste spécifique
  Un récepteur d’événements de l’instance de liste répond aux événements qui se produisent dans une instance d’une définition de liste. Bien que le modèle de récepteur d’événements ne permette pas le ciblage d’une instance de liste spécifique, vous pouvez modifier un récepteur d’événements dont l’étendue correspond à une définition de liste pour répondre aux événements dans une instance de liste spécifique.

 Pour cibler une instance de liste spécifique, dans le *Elements.xml* pour le récepteur d’événements, remplacez `ListTemplateId` par `ListUrl` et ajoutez l’URL de l’instance de liste.

## <a name="create-a-list-instance-event-receiver"></a>Créer un récepteur d’événements d’instance de liste
 Les étapes suivantes montrent comment modifier un récepteur d’événements de liste pour répondre uniquement aux événements qui se produisent dans une instance de liste d’annonces personnalisée.

#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>Pour modifier un récepteur d’événements afin qu’il réponde à une instance de liste spécifique

1. Dans un navigateur, ouvrez le site SharePoint.

2. Dans le volet de navigation, **liste** liens.

3. Dans la page **tout le contenu du site** , choisissez le lien **créer** .

4. Dans la boîte de dialogue **créer** , choisissez le type **annonces** , nommez l’annonce **TestAnnouncements**, puis cliquez sur le bouton **créer** .

5. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , créez un projet de récepteur d’événements.

6. Dans la liste **quel type de récepteur d’événements souhaitez-vous ?** , choisissez **liste des événements d’élément**.

    > [!NOTE]
    > Vous pouvez également sélectionner tout autre type de récepteur d’événements qui correspond à une définition de liste, par exemple **répertorier les événements de courrier électronique** ou **répertorier les événements de workflow**.

7. Dans la liste **quel élément doit être la source de l’événement ?** , choisissez **annonces**.

8. Dans la liste **gérer les événements suivants** , activez la case à cocher **un élément est en cours d’ajout** , puis choisissez le bouton **Terminer** .

9. Dans **Explorateur de solutions**, sous EventReceiver1, ouvrez *Elements.xml*.

     Le récepteur d’événements référence actuellement la définition de liste d’annonces en utilisant la ligne suivante :

    ```xml
    <Receivers ListTemplateId="104">
    ```

     Remplacez cette ligne par le texte suivant :

    ```xml
    <Receivers ListUrl="Lists/TestAnnouncements">
    ```

     Cela indique au récepteur d’événements de répondre uniquement aux événements qui se produisent dans la nouvelle liste d’annonces **TestAnnouncements** que vous venez de créer. Vous pouvez modifier l' `ListURL` attribut pour référencer n’importe quelle instance de liste sur le serveur SharePoint.

10. Ouvrez le fichier de code du récepteur d’événements et placez un point d’arrêt dans la méthode ItemAdding.

11. Appuyez sur la touche **F5** pour générer et exécuter la solution.

12. Dans SharePoint, choisissez le lien **TestAnnouncements** dans le volet de navigation.

13. Choisissez le lien **Ajouter une nouvelle annonce** .

14. Entrez un titre pour l’annonce, puis choisissez le bouton **Enregistrer** .

     Notez que le point d’arrêt est atteint lorsque le nouvel élément est ajouté à la liste d’annonces personnalisée.

15. Appuyez sur la touche **F5** pour reprendre.

16. Dans le volet de navigation, choisissez le lien **listes** , puis choisissez le lien **annonces** .

17. Ajoutez une nouvelle annonce.

     Notez que le récepteur d’événements ne se déclenche pas sur la nouvelle annonce car le récepteur est configuré pour répondre uniquement aux événements de l’instance de liste d’annonces personnalisée, **TestAnnouncements**.

## <a name="see-also"></a>Voir aussi
- [Comment : créer un récepteur d’événements](../sharepoint/how-to-create-an-event-receiver.md)
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
