---
title: 'Comment : ajouter un descripteur de filtre à une méthode de recherche | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 307759881c6795d33dfb5a1c1425402aece05efb
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766612"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Comment : ajouter un descripteur de filtre à une méthode de recherche
  Descripteurs de filtre permettent aux consommateurs du modèle de passer des valeurs aux méthodes avant leur exécution. Pour plus d’informations, consultez [vous concevez un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Un scénario courant est que les utilisateurs de SharePoint récupérer des instances d’un type de contenu externe qui correspondent à certains critères. Vous pouvez prendre en charge ce scénario en ajoutant un descripteur de filtre à une méthode de recherche.  
  
### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Pour ajouter un descripteur de filtre à une méthode de recherche  
  
1.  Dans le **détails de méthode BDC** fenêtre, développez le nœud d’une méthode de recherche, le **paramètres** nœud, puis ajoutez un paramètre d’entrée. Pour plus d’informations, consultez [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md).  
  
2.  Dans le **détails de méthode** fenêtre, choisissez le descripteur de type du paramètre.  
  
3.  Dans la barre de menus, choisissez **vue** > **fenêtre Propriétés**.  
  
4.  Dans le **propriétés** , configurez la **nom de Type** propriété à un type de données qui est approprié pour le filtre.  
  
     Par exemple, un filtre peut utiliser une date de commande pour limiter le nombre de commandes client retournées par la méthode. Pour prendre en charge que le filtre, le **nom de Type** propriété du descripteur de type doit être définie sur **System.DateTime**.  
  
5.  Dans le **détails de méthode** fenêtre, développez le **descripteurs de filtre** nœud.  
  
6.  Dans **ajouter un descripteur de filtre** , choisissez **créer un descripteur de filtre**.  
  
     Un nouveau descripteur de filtre apparaît sous le **descripteurs de filtre** nœud.  
  
7.  Dans la barre de menus, choisissez **vue** > **fenêtre Propriétés**.  
  
8.  Dans le **propriétés** fenêtre, choisissez le **Type** propriété.  
  
9. Dans la liste qui s’affiche pour le **Type** propriété, choisissez le modèle de filtrage que vous le souhaitez.  
  
     Par exemple, pour créer un filtre qui utilise une date de commande pour limiter le nombre de commandes client retournées dans une méthode de recherche, choisissez **comparaison**. Un filtre de comparaison permet de s’assurer qu’une méthode de recherche retourne uniquement les instances qui satisfont à une condition spécifique. Pour plus d’informations sur chaque modèle de filtrage, consultez [Types de filtres pris en charge par le catalogue de données métiers](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
10. Dans le **propriétés** fenêtre, choisissez le **descripteurs de Type associés** propriété.  
  
11. Dans la liste qui s’affiche pour le **descripteurs de Type associés** propriété, choisissez le descripteur de type que vous avez créé précédemment dans cette procédure. Cela lie le filtre au paramètre d’entrée de la méthode de recherche.  
  
12. Ajoutez le code à la méthode de recherche qui retourne des données. Vous pouvez utiliser le paramètre d’entrée comme condition dans une requête select.  
  
     L’exemple suivant retourne les commandes dont la date de commande spécifié.  
  
    > [!NOTE]  
    >  Remplacez la valeur de la `ServerName` champ avec le nom de votre serveur.  
  
     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]  
  
## <a name="see-also"></a>Voir aussi
 [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)   
 [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Comment : définir le descripteur de Type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Conception d’un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  