---
title: 'Comment : ajouter un descripteur de filtre à une méthode de recherche | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f9dd853142d970cd14de20f4782accb3ce3e17eb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986247"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Comment : ajouter un descripteur de filtre à une méthode de recherche
  Les descripteurs de filtre permettent aux consommateurs du modèle de passer des valeurs aux méthodes avant leur exécution. Pour plus d’informations, consultez [concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).

 Un scénario courant est que les utilisateurs de SharePoint souhaitent récupérer des instances d’un type de contenu externe qui correspondent à certains critères. Vous pouvez prendre en charge ce scénario en ajoutant un descripteur de filtre à une méthode de recherche.

### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Pour ajouter un descripteur de filtre à une méthode de recherche

1. Dans la fenêtre **Détails de méthode BDC** , développez le nœud d’une méthode de recherche, développez le nœud **paramètres** , puis ajoutez un paramètre d’entrée. Pour plus d’informations, consultez [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md).

2. Dans la fenêtre **Détails de méthode** , choisissez le descripteur de type du paramètre.

3. Dans la barre de menus, choisissez **afficher** > **fenêtre Propriétés**.

4. Dans la fenêtre **Propriétés** , définissez la propriété **nom du type** sur un type de données approprié pour le filtre.

     Par exemple, un filtre peut utiliser une date de commande pour limiter le nombre de commandes retournées par la méthode. Pour prendre en charge ce filtre, la propriété **nom de type** du descripteur de type doit être définie sur **System. DateTime**.

5. Dans la fenêtre Détails de la **méthode** , développez le nœud **descripteurs de filtre** .

6. Dans **la liste ajouter un descripteur de filtre** , choisissez **créer un descripteur de filtre**.

     Un nouveau descripteur de filtre apparaît sous le nœud **descripteurs de filtre** .

7. Dans la barre de menus, choisissez **afficher** > **fenêtre Propriétés**.

8. Dans la fenêtre **Propriétés** , choisissez la propriété **type** .

9. Dans la liste qui s’affiche pour la propriété **type** , choisissez le modèle de filtrage souhaité.

     Par exemple, pour créer un filtre qui utilise une date de commande afin de limiter le nombre de commandes retournées dans une méthode de recherche, choisissez **comparaison**. Un filtre de comparaison garantit qu’une méthode de recherche ne retourne que les instances qui remplissent une condition spécifique. Pour plus d’informations sur chaque modèle de filtrage, consultez [types de filtres pris en charge par le CDM](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14)).

10. Dans la fenêtre **Propriétés** , choisissez la propriété **descripteurs de type associés** .

11. Dans la liste qui s’affiche pour la propriété **descripteurs de type associés** , choisissez le descripteur de type que vous avez créé précédemment dans cette procédure. Cela associe le filtre au paramètre d’entrée de la méthode Finder.

12. Ajoutez du code à la méthode de recherche qui retourne des données. Vous pouvez utiliser le paramètre d’entrée comme condition dans une requête SELECT.

     L’exemple suivant retourne les commandes client qui ont la date de commande spécifiée.

    > [!NOTE]
    > Remplacez la valeur du champ `ServerName` par le nom de votre serveur.

     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]

## <a name="see-also"></a>Voir aussi
- [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)
- [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Comment : définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
