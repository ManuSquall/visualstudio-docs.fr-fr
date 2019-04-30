---
title: Configurer les informations d’authentification nommées | Microsoft Docs
description: Découvrez comment fournir des informations d’identification que Visual Studio pourra utiliser pour authentifier les demandes effectuées auprès d’Azure, afin que vous puissiez publier une application dans Azure à partir de Visual Studio ou surveiller un service cloud existant.
author: ghogen
manager: jillfra
assetId: 61570907-42a1-40e8-bcd6-952b21a55786
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 23abafcae0e777216a8880adc05ecac38d5b3f0f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961948"
---
# <a name="set-up-named-authentication-credentials"></a>Configurer des informations d’identification d’authentification nommées

Pour publier une application sur Azure ou pour surveiller un service cloud existant, Visual Studio requiert des informations d'identification pour authentifier les demandes auprès d'Azure, à savoir votre ID d'abonnement Azure et un certificat X.509 v3 valide avec une clé d'au moins 2048 bits. Vous pouvez fournir ces informations d'identification à l’aide de l’une des méthodes suivantes :

- Dans Visual Studio, sélectionnez **Affichage > Explorateur de serveurs**, cliquez avec le bouton droit sur le nœud **Azure**, sélectionnez **Se connecter à un abonnement Microsoft Azure**, puis connectez-vous.
- Créez un fichier d'abonnement (`.publishsettings`), contenant une clé publique pour le certificat. Le fichier d’abonnement peut contenir des informations d’identification pour plusieurs abonnements, comme décrit dans cet article.

Remarque: ces informations d'identification sont différentes de celles utilisées pour authentifier les demandes auprès des services de stockage Azure.

## <a name="create-a-subscription-file"></a>Création d’un fichier d'abonnement

Dans l’Explorateur de serveurs, cliquez avec le bouton droit sur le nœud **Azure**, puis sélectionnez **Gérer et filtrer les abonnements**. Sélectionnez ensuite l’onglet **Certificats**, puis effectuez une des actions suivantes :

- Sélectionnez **Importer** pour ouvrir la boîte de dialogue **Importer les abonnements Microsoft Azure**. Sélectionnez le lien **Télécharger le fichier d'abonnement** puis, dans le navigateur, enregistrez le fichier téléchargé dans un emplacement temporaire. Retournez dans la boîte de dialogue, accédez au répertoire d'installation puis importez le fichier afin de l'utiliser pour l'authentification.
- Choisissez un abonnement actif puis sélectionnez **Modifier** afin d'ouvrir une boîte de dialogue dans laquelle vous pouvez modifier un abonnement existant à utiliser pour l'authentification.
- Sélectionnez **Nouveau** pour ouvrir la boîte de dialogue **Nouvel abonnement** puis fournissez les informations requises. Pour télécharger le certificat sur votre service cloud, connectez-vous au portail Azure, accédez à votre service cloud, sélectionnez **Paramètres > Certificats de gestion**, sélectionnez **Charger**, puis spécifiez le chemin d'accès au fichier `.cer`.

Si vous souhaitez créer vous-même un certificat, vous pouvez consulter les instructions fournies dans [Créer et charger un certificat de gestion pour Azure](https://msdn.microsoft.com/library/windowsazure/gg551722.aspx), puis charger manuellement le certificat sur le [portail Azure](https://portal.azure.com/).

## <a name="next-steps"></a>Étapes suivantes

- [Vue d’ensemble de Web Apps](https://docs.microsoft.com/azure/app-service/)
- [Déploiement de votre application dans Azure App Service](https://docs.microsoft.com/azure/app-service/app-service-deploy-local-git) 
- [Déployer WebJobs avec Visual Studio](https://docs.microsoft.com/azure/app-service/websites-dotnet-deploy-webjobs)
- [Création et déploiement d’un service cloud](https://docs.microsoft.com/azure/cloud-services/cloud-services-how-to-create-deploy-portal)