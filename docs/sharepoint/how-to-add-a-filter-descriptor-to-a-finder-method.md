---
title: 'Procédure : Ajouter un descripteur de filtre à une méthode de recherche | Microsoft Docs'
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
ms.openlocfilehash: ee555376a2943cb29344aad2ed94da2b8ab2ae36
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617780"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Procédure : Ajouter un descripteur de filtre à une méthode de recherche
  Descripteurs de filtre permettent aux consommateurs du modèle transmettre des valeurs aux méthodes avant leur exécution. Pour plus d’informations, consultez [concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).

 Un scénario courant est que les utilisateurs de SharePoint récupérer les instances d’un type de contenu externe qui correspondent à certains critères. Vous pouvez prendre en charge ce scénario en ajoutant un descripteur de filtre à une méthode de recherche.

### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Pour ajouter un descripteur de filtre à une méthode de recherche

1.  Dans le **détails de méthode BDC** fenêtre, développez le nœud d’une méthode de recherche, développez le **paramètres** nœud, puis ajoutez un paramètre d’entrée. Pour plus d'informations, voir [Procédure : Ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md).

2.  Dans le **détails de la méthode** fenêtre, choisissez le descripteur de type du paramètre.

3.  Dans la barre de menus, choisissez **vue** > **fenêtre Propriétés**.

4.  Dans le **propriétés** fenêtre, définissez la **nom de Type** propriété à un type de données qui est approprié pour le filtre.

     Par exemple, un filtre peut utiliser une date de commande pour limiter le nombre de commandes client retournées par la méthode. Pour prendre en charge ce filtre, le **nom de Type** propriété du descripteur de type doit être définie sur **System.DateTime**.

5.  Dans le **détails de la méthode** fenêtre, développez le **descripteurs de filtre** nœud.

6.  Dans **ajouter un descripteur de filtre** , choisissez **créer un descripteur de filtre**.

     Un nouveau descripteur de filtre apparaît sous le **descripteurs de filtre** nœud.

7.  Dans la barre de menus, choisissez **vue** > **fenêtre Propriétés**.

8.  Dans le **propriétés** fenêtre, choisissez le **Type** propriété.

9. Dans la liste qui s’affiche pour le **Type** propriété, choisissez le modèle de filtrage que vous le souhaitez.

     Par exemple, pour créer un filtre qui utilise une date de commande pour limiter le nombre de commandes client retournées dans une méthode de recherche, choisissez **comparaison**. Un filtre de comparaison permet de s’assurer qu’une méthode de recherche retourne uniquement les instances qui remplissent une condition spécifique. Pour plus d’informations sur chaque modèle de filtrage, consultez [Types de filtres pris en charge par le BDC](http://go.microsoft.com/fwlink/?LinkId=169287).

10. Dans le **propriétés** fenêtre, choisissez le **descripteurs de Type associés** propriété.

11. Dans la liste qui s’affiche pour le **descripteurs de Type associés** propriété, choisissez le descripteur de type que vous avez créé précédemment dans cette procédure. Le paramètre d’entrée de la méthode de recherche concerne le filtre.

12. Ajoutez le code à la méthode de recherche qui retourne des données. Vous pouvez utiliser le paramètre d’entrée comme une condition dans une requête select.

     L’exemple suivant retourne les commandes qui ont la date de commande spécifié.

    > [!NOTE]
    >  Remplacez la valeur de la `ServerName` champ avec le nom de votre serveur.

     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)
- [Guide pratique pour Ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Guide pratique pour Ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Guide pratique pour Définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
