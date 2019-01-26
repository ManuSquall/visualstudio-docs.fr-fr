---
title: 'Procédure pas à pas : Ajout de récepteurs d’événements de fonctionnalité | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9701281ed6b6e84a3147d6fdeda9ce045fcb5305
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865292"
---
# <a name="walkthrough-add-feature-event-receivers"></a>Procédure pas à pas : Ajout de récepteurs d’événements de fonctionnalité
  Récepteurs d’événements sont des méthodes qui s’exécutent lorsque les événements de fonctionnalité suivants se produisent dans SharePoint :

- Une fonctionnalité est installée.

- La fonctionnalité est activée.

- Une fonctionnalité est désactivée.

- Une fonction est supprimée.

  Cette procédure pas à pas montre comment ajouter un récepteur d’événements à une fonctionnalité dans un projet SharePoint. Il illustre les tâches suivantes :

- Création d’un projet vide avec un récepteur d’événements de fonctionnalité.

- Gérer le **FeatureDeactivating** (méthode).

- À l’aide du modèle objet de projet SharePoint pour ajouter une annonce à la liste d’annonces.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

-   Éditions prises en charge de Microsoft Windows et SharePoint.

-   Visual Studio.

## <a name="create-a-feature-event-receiver-project"></a>Créer un projet de récepteur de fonctionnalité événement
 Tout d’abord, créez un projet pour qu’il contienne le récepteur d’événements de fonctionnalité.

#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>Pour créer un projet avec un récepteur d’événements de fonctionnalité

1.  Dans la barre de menus, choisissez **fichier** > **New** > **projet** pour afficher le **nouveau projet** boîte de dialogue.

2.  Développez le **SharePoint** nœud sous **Visual C#** ou **Visual Basic**, puis choisissez le **2010** nœud.

3.  Dans le **modèles** volet, choisissez le **projet SharePoint 2010** modèle.

     Vous utilisez ce type de projet pour récepteurs d’événements de fonctionnalité, car ils n’ont à aucun modèle de projet.

4.  Dans le **nom** , entrez **TestÉvénementFonctionnalité**, puis choisissez le **OK** bouton pour afficher la **Assistant Personnalisation de SharePoint**.

5.  Sur le **spécifier le niveau de site et de sécurité pour le débogage** page, entrez l’URL pour le site de serveur SharePoint auquel vous souhaitez ajouter le nouvel élément de champ personnalisé ou utilisez l’emplacement par défaut (http://\<*système nom*> /).

6.  Dans le **quel est le niveau de confiance de cette solution SharePoint ?** , choisissez le **déployer en tant que solution de batterie** case d’option.

     Pour plus d’informations sur les solutions bac à sable par rapport aux solutions de batterie de serveurs, consultez [considérations relatives à la solution bac à sable](../sharepoint/sandboxed-solution-considerations.md).

7.  Choisissez le **Terminer** bouton et notez qu’une fonctionnalité qui est nommée Feature1 apparaît sous le **fonctionnalités** nœud.

## <a name="add-an-event-receiver-to-the-feature"></a>Ajouter un récepteur d’événements à la fonctionnalité
 Ensuite, ajoutez un récepteur d’événements à la fonctionnalité et ajouter le code qui s’exécute lorsque la fonctionnalité est désactivée.

#### <a name="to-add-an-event-receiver-to-the-feature"></a>Pour ajouter un récepteur d’événements à la fonctionnalité

1.  Ouvrez le menu contextuel du nœud fonctionnalités, puis choisissez **ajouter une fonctionnalité** pour créer une fonction.

2.  Sous le **fonctionnalités** nœud, ouvrez le menu contextuel pour **Feature1**, puis choisissez **ajouter un récepteur d’événement** pour ajouter un récepteur d’événements à la fonctionnalité.

     Cette opération ajoute un fichier de code sous Feature1. Dans ce cas, il est nommé *Feature1.EventReceiver.cs* ou *Feature1.EventReceiver.vb*, en fonction de langage de développement de votre projet.

3.  Si votre projet est écrit [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)], ajoutez le code suivant en haut du récepteur d’événements si elle n’est pas déjà :

     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]

4.  La classe de récepteur d’événements contient plusieurs méthodes commentées qui agissent en tant qu’événements. Remplacez le **FeatureDeactivating** méthode par le code suivant :

     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]

## <a name="test-the-feature-event-receiver"></a>Tester le récepteur d’événements de fonctionnalité
 Ensuite, désactiver la fonctionnalité pour tester si le **FeatureDeactivating** méthode produit une annonce dans la liste d’annonces de SharePoint.

#### <a name="to-test-the-feature-event-receiver"></a>Pour tester le récepteur d’événements de fonctionnalité

1.  Définissez la valeur du projet **Configuration de déploiement Active** propriété **aucune Activation**.

     Cette propriété empêche la fonctionnalité d’activation dans SharePoint et vous permet de déboguer les récepteurs d’événements de fonctionnalité. Pour plus d’informations, consultez [solutions SharePoint déboguer](../sharepoint/debugging-sharepoint-solutions.md).

2.  Choisissez le **F5** clé pour exécuter le projet et le déployer sur SharePoint.

3.  En haut de la page Web de SharePoint, ouvrez le **Actions du Site** menu, puis choisissez **paramètres du Site**.

4.  Sous le **Actions du Site** section de la **paramètres du Site** page, choisissez le **gérer les fonctionnalités du site** lien.

5.  Sur le **fonctionnalités** page, choisissez le **activer** situé en regard du **FeatureEvtTest Feature1** fonctionnalité.

6.  Sur le **fonctionnalités** page, choisissez le **désactiver** situé en regard le **FeatureEvtTest Feature1** fonctionnalité, puis choisissez le **désactiver cette fonctionnalité**  lien de confirmation pour désactiver la fonctionnalité.

7.  Choisissez le **accueil** bouton.

     Notez qu’une annonce apparaît dans le **annonces** liste une fois la fonctionnalité est désactivée.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Créer un récepteur d’événements](../sharepoint/how-to-create-an-event-receiver.md)
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)