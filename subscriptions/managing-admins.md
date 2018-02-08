---
title: "Gestion des droits d’administrateur dans le portail d’administration des abonnements Visual Studio"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/19/2018
Ms.topic: Get-Started-Article
Description: Learn how manage admins & super admins in the Visual Studio Subscriptions Administrator Portal.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 83bf27d5aaa99c2095ad8a1fafd7541df90f316b
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="managing-administrator-rights-in-the-visual-studio-subscriptions-administrator-portal"></a>Gestion des droits d’administrateur dans le portail d’administration des abonnements Visual Studio

## <a name="overview"></a>Vue d'ensemble 
Dans le portail d’administration des abonnements Visual Studio (https://manage.visualstudio.com), il existe deux rôles de gestion :

**Super administrateurs :** à la création d’une organisation, le contact principal ou le destinataire des avis devient super administrateur par défaut. Le contact principal ou destinataire des avis peut choisir d’assigner des super administrateurs ou administrateurs supplémentaires. En plus de gérer les abonnements d’abonnés individuels, les super administrateurs peuvent ajouter et supprimer d’autres administrateurs et super administrateurs. S’il y a plus de deux super administrateurs définis dans le système, un super administrateur peut en supprimer, mais il doit en conserver au minimum deux pour des raisons de sécurité. 

**Administrateurs :** un administrateur peut gérer les abonnés dans les contrats que le super administrateur lui attribue.  Il peut affecter des abonnements à des personnes, modifier des abonnements, et les réaffecter ou les supprimer.   (Les administrateurs sont désignés par les super administrateurs.)  

## <a name="adding-an-administrator-with-super-admin-rights"></a>Ajout d’un administrateur **avec** des droits de super administrateur :

1. Connectez-vous au [portail d’administration](https://manage.visualstudio.com) des abonnements Visual Studio à travers un compte disposant déjà de droits de super administrateur.

2. Cliquez sur l’onglet **Gérer les administrateurs** en haut de la page. (Seuls les super administrateurs ont accès à cet onglet.  Les administrateurs sans droits de super administrateur doivent utiliser l’onglet **Gérer les abonnés** pour gérer des abonnés individuels.)

3. Cliquez sur **Ajouter** pour créer un nouvel administrateur. 

4. Entrez toutes les informations requises dans la fenêtre indépendante Ajouter un administrateur.
  - Si votre organisation est déjà inscrite dans Azure Active Directory (AAD), commencez à taper le nom dans le champ **Nom**, puis sélectionnez l’élément correct dans la liste déroulante. S’il s’agit de nouveaux utilisateurs, tapez le nom complet et ignorez la notification *Identités introuvables*.
  - Dès que l’utilisateur correct a été identifié, le champ Adresse électronique de connexion est automatiquement renseigné. Entrez l’adresse e-mail du nouvel administrateur, si ce n’est déjà fait.

5. Sélectionnez le **PCN** que vous souhaitez que le nouvel administrateur gère, en cliquant sur la liste déroulante sous **Contrats**. Si le PCN que vous intégrez est associé à plusieurs contrats, vous pouvez donner à votre administrateur l’accès à une partie seulement ou à l’ensemble de ces contrats. 

**Informations supplémentaires sur les contrats :** la fonctionnalité de liste déroulante sous Contrats est désactivée quand seul un contrat est disponible.  Tous les contrats sont automatiquement vérifiés quand vous accordez des droits de super administrateur à l’utilisateur que vous configurez.

6. Cochez la case **Super administrateur** pour activer les droits de super administrateur pour cet administrateur.  

7. Pour confirmer l’ajout de cet administrateur, cliquez sur **Ajouter**.

**Réception d’un message d’erreur potentielle durant l’ajout d’administrateurs :** certains utilisateurs peuvent recevoir un message d’erreur quand ils tentent d’ajouter un administrateur. Ce cas peut se produire si l’adresse e-mail de super administrateur qui est ajoutée ne figure pas dans la liste AAD de l’entreprise. Pour confirmer l’ajout du nouvel administrateur, ignorez simplement l’erreur et cliquez de nouveau sur **Ajouter**. 

8. Après la création d’un super administrateur, celui-ci apparaît dans la liste des administrateurs, et son compte est marqué d’une coche verte pour indiquer son état de super administrateur. 

### <a name="optional--add-a-different-notification-email"></a>Facultatif : ajoutez un autre e-mail de notification.
Si votre organisation possède une autre adresse/compte pour la réception des e-mails, vous avez désormais la possibilité d’entrer une adresse de « communication ». Sélectionnez l’option permettant d’**ajouter un autre e-mail de notification pour la réception des communications**. 

*Exemple :* René utilise rene@contoso.com pour se connecter à l’aide de ses informations d’identification d’entreprise.  Cependant, l’entreprise de René utilise uniquement cette adresse pour gérer l’accès à l’annuaire.  Pour l’envoi et la réception d’e-mails, René utilise rene.collado@contoso.com, de telle sorte que son super administrateur a entré une deuxième adresse pour qu’il reçoive correctement les messages de bienvenue.  Si votre entreprise n’est pas configurée de cette manière, la saisie de l’adresse électronique de connexion devrait être suffisante.

## <a name="adding-an-administrator-without-super-admin-rights"></a>Ajout d’un administrateur **sans** droits de super administrateur :

Le processus décrit précédemment doit être suivi pour ajouter des administrateurs sans droits de super administrateur, en tenant toutefois compte des points suivants :
-  Quand vous ajoutez des administrateurs sans droits de super administrateur, il n’est pas nécessaire d’ajouter une adresse e-mail supplémentaire, et la case à cocher Super administrateur doit rester vide.
-  L’entrée de configuration de profil des utilisateurs sans droits de super administrateur sous « Gérer les administrateurs » n’est pas marquée d’une coche verte.
