---
title: 'Comment : créer un récepteur d’événements | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.SPE.EventReceiver
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 26d8c9f433fad051716b6ebd37e3d1f3b3f9f4eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016925"
---
# <a name="how-to-create-an-event-receiver"></a>Comment : créer un récepteur d’événements
  En créant des *récepteurs d’événements*, vous pouvez répondre lorsqu’un utilisateur interagit avec des éléments SharePoint, tels que des listes ou des éléments de liste. Par exemple, le code d’un récepteur d’événements peut être déclenché lorsqu’un utilisateur modifie le calendrier ou supprime un nom d’une liste de contacts. En suivant cette rubrique, vous pouvez apprendre à ajouter un récepteur d’événements à une instance de liste.

 Pour effectuer ces étapes, vous devez avoir installé [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et pris en charge les éditions de Windows et SharePoint. Étant donné que cet exemple nécessite un projet SharePoint, vous devez également avoir terminé la procédure décrite dans la rubrique [procédure pas à pas : créer une colonne de site, un type de contenu et une liste pour SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

## <a name="adding-an-event-receiver"></a>Ajout d’un récepteur d’événements
 Le projet que vous avez créé dans [procédure pas à pas : création d’une colonne de site, d’un type de contenu et d’une liste pour SharePoint comprend des](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) colonnes de site personnalisées, une liste personnalisée et un type de contenu. Dans la procédure suivante, vous allez développer ce projet en ajoutant un gestionnaire d’événements simple (un récepteur d’événements) à une instance de liste pour montrer comment gérer les événements qui se produisent dans les éléments SharePoint, tels que les listes.

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>Pour ajouter un récepteur d’événements à l’instance de liste

1. Ouvrez le projet que vous avez créé dans [procédure pas à pas : création d’une colonne de site, d’un type de contenu et d’une liste pour SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

2. Dans **Explorateur de solutions**, choisissez le nœud de projet SharePoint, nommé **Clinic**.

3. Dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**.

4. Sous **Visual C#** ou **Visual Basic**, développez le nœud **SharePoint** , puis choisissez l’élément **2010** .

5. Dans le volet **modèles** , choisissez **récepteur d’événements**, nommez-le **TestEventReceiver1**, puis choisissez le bouton **OK** .

     L' **Assistant Personnalisation de SharePoint** s’affiche.

6. Dans la liste **quel type de récepteur d’événements souhaitez-vous ?** , choisissez **liste des événements d’élément**.

7. Dans la liste **quel élément doit être la source de l’événement ?** , choisissez **patients (Clinic\Patients)**.

8. Dans la liste **gérer les événements suivants** , activez la case à cocher en regard d' **un élément a été ajouté**, puis choisissez le bouton **Terminer** .

     Le fichier de code du nouveau récepteur d’événements contient une méthode unique nommée `ItemAdded` . À l’étape suivante, vous allez ajouter du code à cette méthode afin que chaque contact soit nommé Scott Brown par défaut.

9. Remplacez la `ItemAdded` méthode existante par le code suivant, puis appuyez sur la touche **F5** :

     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]

     Le code s’exécute et le site SharePoint s’affiche dans le navigateur Web.

10. Dans la barre de lancement rapide, choisissez le lien **patients** , puis choisissez le lien **Ajouter un nouvel élément** .

     Le formulaire d’entrée pour les nouveaux éléments s’ouvre.

11. Entrez des données dans les champs, puis cliquez sur le bouton **Enregistrer** .

     Une fois que vous avez choisi le bouton **Enregistrer** , la colonne **nom du patient** met automatiquement à jour le nom Scott Brown.

## <a name="see-also"></a>Voir aussi

- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)