---
title: Services connectés
description: Ajouter le stockage de données Azure, l’authentification et les notifications Push aux applications mobiles à partir de Visual Studio pour Mac
ms.assetid: 41CB62FF-0F39-4CE8-8917-6A77F058719F
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/06/2018
ms.openlocfilehash: 241820de009a5118869583bbe228ecb0604f9001
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74985289"
---
# <a name="connected-services-walkthrough"></a>Procédure pas à pas des services connectés

Comme le flux de travail Services connectés intègre le flux de travail du portail Azure à Visual Studio pour Mac, vous n’avez pas à quitter votre projet pour ajouter des services.

Cette procédure pas à pas montre comment ajouter un service backend Azure, qui intègre le stockage de données dans le cloud, l’authentification et les notifications Push à une application de bibliothèque de classes portable (PCL) Xamarin.Forms multiplateforme.

1. Commencez par double-cliquer sur le nœud **Services connectés** dans la solution, pour afficher la **galerie des services**.
  Il s’agit d’une liste de tous les services disponibles pour le type d’application. Sélectionnez un service (tel que **Backend mobile avec Azure App Service**) en cliquant dessus.

    [![Nœud Services connectés dans Visual Studio pour Mac](media/connected-services-image001-sml.png "Nœud Services connectés dans Visual Studio pour Mac")](media/connected-services-image001.png#lightbox)

2. La page Détails sur le service comporte une description du service et des dépendances à installer.
  Cliquez sur le bouton **Ajouter** pour ajouter les dépendances à l’application :

    [![Backend mobile avec Azure](media/connected-services-image002-sml.png "Backend mobile avec Azure")](media/connected-services-image002.png#lightbox)

3. Les dépendances doivent être ajoutées à la fois à la bibliothèque PCL et aux projets spécifiques à une plateforme pour fonctionner.
  Cochez les cases pour ajouter le service à chaque projet qui le référence (directement ou indirectement) :

    [![Vérifier tous les projets qui doivent référencer le service](media/connected-services-image003-sml.png "Vérifier tous les projets qui doivent référencer le service")](media/connected-services-image003.png#lightbox)

4. Choisissez **Accepter** dans les boîtes de dialogue **Acceptation de la licence** pour les packages NuGet.
  Deux boîtes de dialogue avec l’option Accepter peuvent s’afficher : une pour MobileClient et les dépendances, et une autre pour SQLiteStore, ce qui est nécessaire pour la synchronisation de données hors connexion :

    [![Accepter les contrats de licence](media/connected-services-image004-sml.png "Accepter les contrats de licence")](media/connected-services-image004.png#lightbox)

    ![Fenêtre acceptation de la licence](media/connected-services-image005.png "Fenêtre acceptation de la licence")

5. Une fois que les dépendances sont ajoutées, vous êtes invité à vous connecter avec le compte que vous voulez utiliser pour communiquer avec Azure.
  Si vous êtes déjà connecté avec un ID Microsoft, Visual Studio pour Mac va tenter de récupérer vos abonnements Azure et tous les App Services qui s’y rapportent. Si vous n’avez aucun abonnement, vous pouvez en ajouter un en vous inscrivant pour un essai gratuit ou en achetant un plan d’abonnement dans le portail Azure.

6. Sélectionnez un App Service dans la liste. Cela remplira le code du modèle pour l’objet `MobileServiceClient` avec l’URL correspondante de l’App Service sur Azure :

    [![Sélectionner App service dans la liste](media/connected-services-image006-sml.png "Sélectionner App service dans la liste")](media/connected-services-image006.png#lightbox)

    Si aucun service n’est répertorié, cliquez sur le bouton **Nouveau** (consultez l’étape 9).

7. Copiez le code du modèle pour l’objet `MobileServiceClient` dans la bibliothèque PCL. L’emplacement du fichier n’est pas important tant qu’il n’existe qu’une seule instance de celui-ci.
  L’approche recommandée consiste à créer une classe `AzureService` qui gère toutes les interactions Azure et utilise l’objet `MobileServiceClient` :

    ![Copier le code de configuration dans le point d’accès](media/connected-services-image007.png "Copier le code de configuration dans l’application")

8. Suivez la documentation dans **Étapes suivantes** pour ajouter des données, la synchronisation hors connexion, l’authentification et les notifications Push à votre application :

    [![Passez en revue les instructions suivantes](media/connected-services-image008-sml.png "Passez en revue les instructions suivantes")](media/connected-services-image008.png#lightbox)

9. Si vous n’avez aucun App Service, vous pouvez en créer de nouveaux à partir de Visual Studio pour Mac.
  Cliquez sur le bouton **Nouveau** dans la partie inférieure gauche de la liste des services pour ouvrir la boîte de dialogue **Nouvel App Service** :

    [![Créer un app service dans Visual Studio pour Mac](media/connected-services-image009-sml.png "Créer un app service dans Visual Studio pour Mac")](media/connected-services-image009.png#lightbox)

Un nouveau service nécessite les paramètres suivants :

- **Nom de l’App Service** : ID/nom unique du plan
- **Abonnement** : abonnement que vous souhaitez utiliser pour payer le service
- **Groupe de ressources** : façon d’organiser toutes vos ressources Azure pour un projet. Possibilité d’utiliser l’existant ou d’en créer un autre. S’il s’agit de votre premier service Azure, créez-en un autre.
- **Plan de service** : détermine l’emplacement et le coût des ressources qui l’utilisent. Possibilité d’utiliser l’existant ou d’en créer un autre. S’il s’agit de votre premier service Azure, utilisez celui par défaut ou créez-en un autre dans le niveau gratuit (F1).

Pour plus d’informations, consultez la [documentation sur les applications mobiles](/azure/app-service-mobile/).

## <a name="see-also"></a>Voir aussi

- [Services connectés (Visual Studio sur Windows)](/visualstudio/azure/vs-azure-tools-connected-services-storage)