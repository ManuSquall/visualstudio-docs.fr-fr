---
title: Préparer la publication ou le déploiement d’un service cloud
description: Découvrez les procédures de configuration des services de compte de stockage et cloud et de votre application Azure.
author: ghogen
manager: jillfra
ms.assetid: 92ee2f9e-ec49-4c7a-900d-620abe5e9d8a
ms.prod: visual-studio-dev15
ms.custom: seodec18
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: d5ba083ec762976c744d6cebc9ce3e240f4c9c65
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55139764"
---
# <a name="prepare-to-publish-or-deploy-a-cloud-service-from-visual-studio"></a>Préparer la publication ou le déploiement d’un service cloud à partir de Visual Studio

Pour pouvoir publier un projet de service cloud, vous devez configurer les services suivants, comme décrit dans cet article :

* Un **service cloud** pour exécuter vos rôles dans l'environnement Azure, et
* Un **compte de stockage** qui fournit l'accès aux services Blob, File d'attente et Table.

## <a name="create-a-cloud-service"></a>Création d'un service cloud

Un service cloud exécute vos rôles dans l'environnement Azure. Vous pouvez créer un service cloud dans Visual Studio ou via le [portail Azure](https://portal.azure.com/), comme indiqué dans les sections suivantes.

### <a name="create-a-cloud-service-from-visual-studio"></a>Création d'un service cloud à partir de Visual Studio

1. Dans un projet Service cloud précédemment créé, cliquez avec le bouton droit sur le projet, puis sélectionnez **Publier**.
1. Si nécessaire, connectez-vous avec le compte Microsoft ou de société associé à votre abonnement Azure, puis sélectionnez **Suivant** pour passer à la page **Paramètres**.
1. Une boîte de dialogue **Créer un service cloud et un compte de stockage** s'affiche (si ce n'est pas le cas, sélectionnez **Créer** dans la liste **Service cloud**).
1. Nommez votre service cloud en utilisant un nom qui ne tient pas compte de la casse : ce nom constitue une partie de votre URL et doit être unique. Choisissez également une région ou un groupe d'affinité, puis sélectionnez une option de réplication.

### <a name="create-a-cloud-service-through-the-azure-portal"></a>Création d'un service cloud via le portail Azure

1. Connectez-vous au [portail Azure](https://portal.azure.com/).
1. Sélectionnez **Services cloud (classiques)** sur la partie gauche de la page.
1. Sélectionnez **Ajouter**, puis fournissez les informations requises (nom DNS, abonnement, groupe de ressources et emplacement). Il n'est pas nécessaire de charger un package à ce stade, car vous le ferez plus tard dans Visual Studio.
1. Sélectionnez **Créer** pour terminer le processus.

## <a name="create-a-storage-account"></a>Créez un compte de stockage.

Un compte de stockage fournit l'accès aux services Blob, File d'attente et Table. Vous pouvez créer un compte de stockage via Visual Studio ou le [portail Azure](https://portal.azure.com/).

### <a name="create-a-storage-account-from-visual-studio"></a>Création d'un compte de stockage à partir de Visual Studio

1. Dans l'**Explorateur de solutions**, avec un projet de service cloud précédemment créé, recherchez le nœud **Services connectés** dans un projet de rôle, cliquez avec le bouton droit, puis sélectionnez **Ajouter un service connecté**. (Dans Visual Studio 2015, cliquez avec le bouton droit sur le nœud **Stockage**, puis sélectionnez **Créer un compte de stockage**.)
1. Dans la liste **Services connectés** qui apparaît, sélectionnez **Stockage cloud avec le Stockage Azure**.
1. Dans la boîte de dialogue Stockage Azure qui apparaît, sélectionnez **Créer un compte de stockage**, pour afficher une boîte de dialogue dans laquelle vous pouvez spécifier votre abonnement, le nom du compte, un niveau de tarification, un groupe de ressources et un emplacement.
1. Sélectionnez **Créer** lorsque vous avez terminé. Le nouveau compte de stockage apparaît dans la liste des comptes de stockage disponibles dans votre abonnement.
1. Sélectionnez ce compte, puis **Ajouter**.

### <a name="create-a-storage-account-through-the-azure-portal"></a>Création d'un compte de stockage via le portail Azure

1. Connectez-vous au [portail Azure](https://portal.azure.com/).
1. Sélectionnez **+ Nouveau** dans le coin supérieur gauche.
1. Sélectionnez **Stockage** sous « Place de marché Azure », puis **Compte de stockage - blob, fichier, table, file d'attente** dans la partie droite.
1. Fournissez les informations requises (nom, modèle de déploiement, etc.)
1. Sélectionnez **Créer** pour terminer le processus.

## <a name="configure-your-app-to-use-the-storage-account"></a>Configuration de votre application pour utiliser le compte de stockage

Après avoir créé un compte de stockage, la connexion à partir de Visual Studio met automatiquement à jour les configurations de service pour le projet, y compris les URL et les clés d'accès.

Si vous avez créé un service cloud à partir de Visual Studio à l'aide de l'option **Ajouter un service connecté**, vous pouvez vérifier les connexions en ouvrant `ServiceConfiguration.Cloud.cscfg` et `ServiceConfiguration.Local.cscfg`.

Si vous avez créé un service cloud via le portail Azure, suivez les mêmes étapes de la section [Création d'un compte de stockage à partir de Visual Studio](#create-a-storage-account-from-visual-studio), en sélectionnant le compte existant au lieu d'en créer un. Ensuite, Visual Studio met à jour la configuration pour vous.

Pour configurer les paramètres manuellement, utilisez les pages de propriétés de Visual Studio pour le rôle applicable dans votre projet de service cloud (cliquez avec le bouton droit sur le rôle et sélectionnez **Propriétés**). Pour plus d'informations, voir [Configuration d’une chaîne de connexion à un compte de stockage](vs-azure-tools-multiple-services-project-configurations.md#configuring-a-connection-string-for-a-storage-account).

### <a name="about-access-keys"></a>À propos des clés d'accès

Le portail Azure affiche les URL que vous pouvez utiliser pour accéder aux ressources dans chacun des services de stockage Azure, ainsi que les clés d'accès primaire et secondaire de votre compte. Ces clés vous permettent d'authentifier des demandes adressées aux services de stockage.

La clé d'accès secondaire fournit le même accès à votre compte de stockage que la clé d'accès primaire et est générée comme sauvegarde au cas où votre clé primaire serait compromise. En outre, il est recommandé de régénérer régulièrement vos clés d'accès. Vous pouvez modifier un paramètre de la chaîne de connexion pour utiliser la clé secondaire pendant que vous régénérez la clé primaire, puis vous pouvez le modifier pour utiliser la clé primaire régénérée pendant que vous régénérez la clé secondaire.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur la publication d’applications entre Visual Studio et Azure, consultez la page [Publication d’un service cloud en utilisant les outils Azure](vs-azure-tools-publishing-a-cloud-service.md).
