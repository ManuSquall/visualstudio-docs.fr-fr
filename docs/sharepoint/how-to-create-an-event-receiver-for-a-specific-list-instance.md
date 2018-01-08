---
title: "Comment : créer un récepteur d’événements pour une Instance de liste spécifique | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
ms.assetid: 4b4b3564-161a-4327-8963-50896c084ac2
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a820bc1a29db10fa5f65f1781c30218c62c2ee08
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>Comment : créer un récepteur d'événements pour une instance de liste spécifique
  Un récepteur d’événements liste instance répond aux événements qui se produisent dans n’importe quelle instance d’une définition de liste. Bien que le modèle de récepteur d’événements n’active pas le ciblage d’une instance de liste spécifique, vous pouvez modifier un récepteur d’événements qui s’étend à une définition de liste pour répondre aux événements dans une instance de liste spécifique.  
  
 Pour cibler une instance de liste spécifique, dans le fichier Elements.xml pour le récepteur d’événements, remplacez `ListTemplateId` avec `ListUrl` et ajoutez l’URL de l’instance de liste.  
  
## <a name="creating-a-list-instance-event-receiver"></a>Création d’un récepteur d’événements liste Instance  
 Les étapes suivantes montrent comment modifier un récepteur d’événements liste élément réponde uniquement aux événements qui se produisent dans une instance de la liste d’annonces personnalisées.  
  
#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>Pour modifier un récepteur d’événements pour répondre à une instance de liste spécifique  
  
1.  Dans un navigateur, ouvrez le site SharePoint.  
  
2.  Dans le volet de navigation, **répertorie** lien.  
  
3.  Dans le **tout le contenu du Site** page, choisissez la **créer** lien.  
  
4.  Dans le **créer** boîte de dialogue, choisissez le **annonces** type, nom de l’annonce **TestAnnouncements**, puis choisissez le **créer**bouton.  
  
5.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], créez un projet de récepteur d’événements.  
  
6.  Dans le **le type de récepteur d’événements voulez-vous ?** , choisissez **événements d’élément de liste**.  
  
    > [!NOTE]  
    >  Vous pouvez également sélectionner n’importe quel autre type de récepteur d’événements qui s’étend sur une définition de liste, par exemple, **liste des événements de messagerie** ou **liste des événements de flux de travail**.  
  
7.  Dans le **quel élément doit être la source d’événements ?** , choisissez **annonces**.  
  
8.  Dans le **gérer les événements suivants** liste, sélectionnez le **Ajout d’un élément** case à cocher, puis choisissez le **Terminer** bouton.  
  
9. Dans **l’Explorateur de solutions**, sous EventReceiver1, ouvre le fichier Elements.xml.  
  
     Le récepteur d’événements fait actuellement référence à la définition de liste d’annonces à l’aide de la ligne suivante :  
  
    ```  
    <Receivers ListTemplateId="104">  
    ```  
  
     Remplacez cette ligne par le texte suivant :  
  
    ```  
    <Receivers ListUrl="Lists/TestAnnouncements">  
    ```  
  
     Il dirige le récepteur d’événements réponde uniquement aux événements qui se produisent dans le nouveau **TestAnnouncements** liste d’annonces que vous venez de créer. Vous pouvez modifier le `ListURL` attribut pour référencer n’importe quelle instance de liste sur le serveur SharePoint.  
  
10. Ouvrez le fichier de code pour le récepteur d’événements et placer un point d’arrêt dans la méthode ItemAdding.  
  
11. Choisissez la touche F5 pour générer et exécuter la solution.  
  
12. Dans SharePoint, choisissez le **TestAnnouncements** lien dans le volet de navigation.  
  
13. Choisissez le **ajouter une nouvelle annonce** lien.  
  
14. Entrez un titre pour l’annonce, puis choisissez le **enregistrer** bouton.  
  
     Notez que le point d’arrêt est atteint lorsque le nouvel élément est ajouté à la liste d’annonces personnalisées.  
  
15. Choisissez la touche F5 pour reprendre.  
  
16. Dans le volet de navigation, choisissez le **répertorie** lier, puis choisissez le **annonces** lien.  
  
17. Ajouter une nouvelle annonce.  
  
     Notez que le récepteur d’événements ne déclenche pas sur la nouvelle annonce car le récepteur est configuré pour répondre uniquement à des événements dans l’instance de liste d’annonces personnalisées, **TestAnnouncements**.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer un récepteur d’événements](../sharepoint/how-to-create-an-event-receiver.md)   
 [Développement de solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  