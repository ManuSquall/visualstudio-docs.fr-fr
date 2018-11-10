---
title: Configurer les informations d’authentification nommées | Microsoft Docs
description: Apprenez à fournir des informations d’identification que Visual Studio peut utiliser pour authentifier les demandes vers Azure, donc vous pouvez publier une application sur Azure à partir de Visual Studio ou surveiller un service cloud existant.
author: ghogen
manager: douge
assetId: 61570907-42a1-40e8-bcd6-952b21a55786
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 6f41ea2072ef5791735fac61205f68151d5a9f7e
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001989"
---
# <a name="set-up-named-authentication-credentials"></a>Configurer des informations d’identification d’authentification nommées

Pour publier une application dans Azure ou pour surveiller un service cloud existant, Visual Studio requiert les informations d’identification pour authentifier les demandes vers Azure, à savoir votre ID d’abonnement Azure et un certificat X.509 v3 valide avec une clé d’au moins 2 048 bits. Vous fournissez ces informations d’identification via une des méthodes suivantes :

- Dans Visual Studio, sélectionnez **Affichage > Explorateur de serveurs**, avec le bouton droit le **Azure** nœud, sélectionnez **se connecter à abonnement Microsoft Azure**et s’y connecter.
- Créer un fichier d’abonnement (`.publishsettings`), qui contient une clé publique pour le certificat. Le fichier d’abonnement peut contenir des informations d’identification pour plusieurs abonnements, comme décrit dans cet article.

Remarque : ces informations d’identification sont différentes des informations d’identification utilisées pour authentifier les demandes aux services de stockage Azure.

## <a name="create-a-subscription-file"></a>Créer un fichier d’abonnement

Dans l’Explorateur de serveurs, cliquez sur le **Azure** nœud et sélectionnez **gérer et filtrer les abonnements**. Puis sélectionnez le **certificats** onglet, puis effectuez l’une des actions suivantes :

- Sélectionnez **importation** pour ouvrir le **importer les abonnements Microsoft Azure** boîte de dialogue. Sélectionnez le **télécharger le fichier abonnement** lien et dans le navigateur, enregistrez le fichier téléchargé dans un emplacement temporaire. Dans la boîte de dialogue, accédez à l’emplacement de téléchargement et puis l’importer pour une utilisation dans l’authentification.
- Choisissez un abonnement actif, puis sélectionnez **modifier**, qui ouvre une boîte de dialogue dans laquelle vous modifier un abonnement existant pour une utilisation dans l’authentification.
- Sélectionnez **New** pour ouvrir le **nouvel abonnement** boîte de dialogue zone et fournissez les informations requises. Pour télécharger le certificat à votre cloud service sont indiquées dans la boîte de dialogue, connectez-vous au portail Azure, accédez à votre service cloud, sélectionnez **Paramètres > certificats de gestion**, sélectionnez **télécharger**, puis Spécifiez le chemin d’accès à la `.cer` fichier.

Si vous souhaitez créer vous-même un certificat, vous pouvez consulter les instructions fournies dans [création et téléchargement d’un certificat de gestion pour Azure](https://msdn.microsoft.com/library/windowsazure/gg551722.aspx) , puis charger manuellement le certificat à la [Azure portal](https://portal.azure.com/).

## <a name="next-steps"></a>Étapes suivantes

- [Vue d’ensemble des applications Web](https://docs.microsoft.com/azure/app-service/)
- [Déployer votre application dans Azure App Service](https://docs.microsoft.com/azure/app-service/app-service-deploy-local-git) 
- [Déployer WebJobs à l’aide de Visual Studio](https://docs.microsoft.com/azure/app-service/websites-dotnet-deploy-webjobs)
- [Créer et déployer un service cloud](https://docs.microsoft.com/azure/cloud-services/cloud-services-how-to-create-deploy-portal)