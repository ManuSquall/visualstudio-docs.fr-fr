---
title: Préparer la publication ou le déploiement d’un Service Cloud à partir de Visual Studio | Microsoft Docs
description: Découvrez les procédures pour configurer le compte de services cloud et de stockage et de configurer votre application Windows Azure.
author: ghogen
manager: douge
ms.assetid: 92ee2f9e-ec49-4c7a-900d-620abe5e9d8a
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: d7643d87f60b953b9c0928571036c7890e4d11f0
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002030"
---
# <a name="prepare-to-publish-or-deploy-a-cloud-service-from-visual-studio"></a>Préparer la publication ou le déploiement d’un service cloud à partir de Visual Studio

Pour publier un projet de service cloud, vous devez configurer les services suivants, comme décrit dans cet article :

* Un **service cloud** pour exécuter vos rôles dans l’environnement Azure, et 
* Un **compte de stockage** qui fournit l’accès aux services Blob, file d’attente et Table.

## <a name="create-a-cloud-service"></a>Créer un service cloud

Un service cloud exécute vos rôles dans l’environnement Azure. Vous pouvez créer un service cloud dans Visual Studio ou via le [Azure portal](https://portal.azure.com/) comme décrit dans les sections qui suivent.

### <a name="create-a-cloud-service-from-visual-studio"></a>Créer un service cloud à partir de Visual Studio

1. Avec un projet de Service Cloud précédemment créé, cliquez sur le projet, sélectionnez **publier**.
1. Si nécessaire, connectez-vous avec le Microsoft ou d’un compte professionnel associé à votre abonnement Azure, puis sélectionnez **suivant** pour accéder à la **paramètres** page.
1. Un **créer un Service Cloud et le compte de stockage** boîte de dialogue s’affiche (dans le cas contraire, sélectionnez **créer un nouveau** à partir de la **Service Cloud** liste).
1. Entrez un nom de non-respect de la casse pour votre service cloud, ce qui constitue une partie de votre URL et doit être unique. Également choisir une région ou un groupe d’affinités, sélectionnez une option de réplication.

### <a name="create-a-cloud-service-through-the-azure-portal"></a>Créer un service cloud via le portail Azure

1. Connectez-vous au [portail Azure](https://portal.azure.com/).
1. Sélectionnez **Services Cloud (classiques)** sur le côté gauche de la page.
1. Sélectionnez **+ ajouter**, puis fournissez les informations requises (DNS nom, abonnement, groupe de ressources et emplacement). Il n’est pas nécessaire télécharger un package à ce stade, car cela plus tard dans Visual Studio.
1. Sélectionnez **créer** pour terminer le processus.

## <a name="create-a-storage-account"></a>Créer un compte de stockage

Un compte de stockage fournit l’accès aux services Blob, file d’attente et Table. Vous pouvez créer un compte de stockage via Visual Studio ou le [Azure portal](https://portal.azure.com/).

### <a name="create-a-storage-account-from-visual-studio"></a>Créer un compte de stockage à partir de Visual Studio

1. Dans **l’Explorateur de solutions** avec un projet de Service Cloud précédemment créé, recherchez le **Services connectés** nœud au sein d’un projet de rôle, avec le bouton droit, puis sélectionnez **ajouter un Service connecté**. (Dans Visual Studio 2015, cliquez sur le **stockage** nœud et sélectionnez **créer un compte de stockage**.)
1. Dans le **Services connectés** liste qui s’affiche, sélectionnez **stockage Cloud avec stockage Azure**.
1. Dans la boîte de dialogue stockage Azure qui s’affiche, sélectionnez **+ créer un compte de stockage**, qui affiche une boîte de dialogue dans laquelle vous spécifiez votre abonnement, le nom du compte, un prix niveau, groupe de ressources et un emplacement.
1. Sélectionnez **créer** lorsque vous avez terminé. Le nouveau compte de stockage apparaît dans la liste des comptes de stockage disponibles dans votre abonnement.
1. Sélectionnez ce compte, sélectionnez **ajouter**.

### <a name="create-a-storage-account-through-the-azure-portal"></a>Créer un compte de stockage via le portail Azure

1. Connectez-vous au [portail Azure](https://portal.azure.com/).
1. Sélectionnez **+ nouveau** en haut à gauche.
1. Sélectionnez **stockage** sous « Place de marché Azure, « puis **compte de stockage - blob, fichier, table, file d’attente** du côté droit.
1. Fournissez les informations requises (nom de modèle de déploiement et ainsi de suite.
1. Sélectionnez **créer** pour terminer le processus.

## <a name="configure-your-app-to-use-the-storage-account"></a>Configurer votre application pour utiliser le compte de stockage

Après avoir créé un compte de stockage, connexion à partir de Visual Studio automatiquement met à jour les configurations de service pour le projet, y compris les URL et les clés d’accès.

Si vous avez créé un service cloud à partir de Visual Studio en utilisant le **ajouter un Service connecté**, vous pouvez vérifier les connexions en ouvrant `ServiceConfiguration.Cloud.cscfg` et `ServiceConfiguration.Local.cscfg`.

Si vous avez créé un service cloud via le portail Azure, suivez les mêmes étapes dans [créer un compte de stockage à partir de Visual Studio](#create-a-storage-account-from-visual-studio) mais sélectionnez le compte existant au lieu de créer un nouveau. Visual Studio met ensuite à jour la configuration pour vous.

Pour configurer les paramètres manuellement, utilisent les pages de propriétés dans Visual Studio pour le rôle applicable dans votre projet de service cloud (cliquez sur le rôle et sélectionnez **propriétés**). Pour plus d’informations, consultez [configuration d’une chaîne de connexion à un compte de stockage](vs-azure-tools-multiple-services-project-configurations.md#configuring-a-connection-string-for-a-storage-account).

### <a name="about-access-keys"></a>À propos des clés d’accès

Le portail Azure affiche les URL que vous pouvez utiliser pour accéder aux ressources dans chacun des services de stockage Azure, ainsi que les clés d’accès primaire et secondaire pour votre compte. Vous utilisez ces clés pour authentifier les demandes adressées aux services de stockage.

La clé d’accès secondaire fournit le même accès à votre compte de stockage que la clé d’accès primaire et est générée sous la forme d’une sauvegarde si votre clé primaire doit être compromis. En outre, il est recommandé que vous régénérez vos clés d’accès sur une base régulière. Vous pouvez modifier un paramètre de chaîne de connexion à utiliser la clé secondaire pendant la régénération de la clé primaire, puis vous pouvez le modifier pour utiliser la clé primaire régénérée pendant la régénération de la clé secondaire.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur la publication des applications vers Azure à partir de Visual Studio, consultez [publication d’un Service Cloud à l’aide de Windows Azure Tools](vs-azure-tools-publishing-a-cloud-service.md).
