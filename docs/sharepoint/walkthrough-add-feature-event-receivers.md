---
title: 'Procédure pas à pas : ajout de récepteurs d’événements de fonctionnalité | Microsoft Docs'
description: Dans cette procédure pas à pas, ajoutez des récepteurs d’événements de fonctionnalité, qui sont des méthodes qui s’exécutent quand une fonctionnalité SharePoint est installée, activée, désactivée ou supprimée.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 98b85222fca4da6dfca653ad74e1315801798d83
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915594"
---
# <a name="walkthrough-add-feature-event-receivers"></a>Procédure pas à pas : ajout de récepteurs d’événements de fonctionnalité
Les récepteurs d’événements de fonctionnalité sont des méthodes qui s’exécutent lorsque l’un des événements suivants liés aux fonctionnalités se produit dans SharePoint :

- Une fonctionnalité est installée.

- Une fonctionnalité est activée.

- Une fonctionnalité est désactivée.

- Une fonctionnalité est supprimée.

Cette procédure pas à pas montre comment ajouter un récepteur d’événements à une fonctionnalité dans un projet SharePoint. Il illustre les tâches suivantes :

- Création d’un projet vide avec un récepteur d’événements de fonctionnalité.

- Gestion de la méthode **FeatureDeactivating** .

- Utilisation du modèle objet de projet SharePoint pour ajouter une annonce à la liste d’annonces.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- Éditions prises en charge de Microsoft Windows et SharePoint.

- Visual Studio.

## <a name="create-a-feature-event-receiver-project"></a>Créer un projet de récepteur d’événements de fonctionnalité
 Tout d’abord, créez un projet pour contenir le récepteur d’événements de fonctionnalité.

#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>Pour créer un projet avec un récepteur d’événements de fonctionnalité

1. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet** pour afficher la boîte de dialogue **nouveau projet** .

2. Développez le nœud **SharePoint** sous **Visual C#** ou **Visual Basic**, puis choisissez le nœud **2010** .

3. Dans le volet **modèles** , choisissez le modèle de **projet SharePoint 2010** .

     Vous utilisez ce type de projet pour les récepteurs d’événements de fonctionnalité, car ils n’ont pas de modèle de projet.

4. Dans la zone **nom** , entrez **FeatureEvtTest**, puis choisissez le bouton **OK** pour afficher l' **Assistant Personnalisation de SharePoint**.

5. Dans la page **spécifier le site et le niveau de sécurité pour le débogage** , entrez l’URL du site du serveur SharePoint auquel vous souhaitez ajouter le nouvel élément de champ personnalisé ou utilisez l’emplacement par défaut (http:// \<*system name*> /).

6. Dans la section **quel est le niveau de confiance de cette solution SharePoint ?** , choisissez la case **d’option déployer en tant que solution de batterie** .

     Pour plus d’informations sur les solutions sandbox et les solutions de batterie de serveurs, consultez Considérations sur les solutions [bac à sable (sandbox)](../sharepoint/sandboxed-solution-considerations.md).

7. Choisissez le bouton **Terminer** , puis notez qu’une fonctionnalité nommée Feature1 apparaît sous le nœud **fonctionnalités** .

## <a name="add-an-event-receiver-to-the-feature"></a>Ajouter un récepteur d’événements à la fonctionnalité
 Ensuite, ajoutez un récepteur d’événements à la fonctionnalité et ajoutez du code qui s’exécute lorsque la fonctionnalité est désactivée.

#### <a name="to-add-an-event-receiver-to-the-feature"></a>Pour ajouter un récepteur d’événements à la fonctionnalité

1. Ouvrez le menu contextuel du nœud fonctionnalités, puis choisissez **Ajouter une fonctionnalité** pour créer une fonctionnalité.

2. Sous le nœud **fonctionnalités** , ouvrez le menu contextuel pour **Feature1**, puis choisissez **Ajouter un récepteur** d’événements pour ajouter un récepteur d’événements à la fonctionnalité.

     Cela ajoute un fichier de code sous Feature1. Dans ce cas, il est nommé *Feature1.EventReceiver.cs* ou *Feature1. EventReceiver. vb*, selon le langage de développement de votre projet.

3. Si votre projet est écrit dans [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] , ajoutez le code suivant en haut du récepteur d’événements s’il n’est pas déjà présent :

     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]

4. La classe de récepteur d’événements contient plusieurs méthodes commentées qui jouent le rôle d’événements. Remplacez la méthode **FeatureDeactivating** par le code suivant :

     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]

## <a name="test-the-feature-event-receiver"></a>Tester le récepteur d’événements de fonctionnalité
 Ensuite, désactivez la fonctionnalité pour tester si la méthode **FeatureDeactivating** génère une annonce dans la liste des annonces SharePoint.

#### <a name="to-test-the-feature-event-receiver"></a>Pour tester le récepteur d’événements de fonctionnalité

1. Définissez la valeur de la propriété de **configuration de déploiement active** du projet sur **aucune activation**.

     La définition de cette propriété empêche la fonctionnalité de s’activer dans SharePoint et vous permet de déboguer des récepteurs d’événements de fonctionnalité. Pour plus d’informations, consultez [Déboguer des solutions SharePoint](../sharepoint/debugging-sharepoint-solutions.md).

2. Appuyez sur la touche **F5** pour exécuter le projet et le déployer sur SharePoint.

3. En haut de la page Web SharePoint, ouvrez le menu **actions du site** , puis choisissez **paramètres du site**.

4. Dans la section **actions** du site de la page **paramètres du site** , choisissez le lien gérer les fonctionnalités du **site** .

5. Dans la page **fonctionnalités** , choisissez le bouton **activer** en regard de la fonctionnalité **FeatureEvtTest Feature1** .

6. Dans la page **fonctionnalités** , choisissez le bouton **Désactiver** en regard de la fonctionnalité **FeatureEvtTest Feature1** , puis choisissez le lien **désactiver cette fonctionnalité** de confirmation pour désactiver la fonctionnalité.

7. Choisissez le bouton **démarrage** .

     Notez qu’une annonce apparaît dans la liste **annonces** une fois que la fonctionnalité est désactivée.

## <a name="see-also"></a>Voir aussi

- [Comment : créer un récepteur d’événements](../sharepoint/how-to-create-an-event-receiver.md)
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)