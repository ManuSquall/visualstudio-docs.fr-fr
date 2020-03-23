---
title: 'Étape 5 : Déployer votre application de base ASP.NET à Azure'
description: Déployez votre application web ASP.NET Core sur Azure avec ce tutoriel vidéo et des instructions détaillées.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: dc13dbdadb0c9bca25a816b15c5a99039bff454c
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580030"
---
# <a name="step-5-deploy-your-aspnet-core-app-to-azure"></a>Étape 5 : Déployez votre application ASP.NET Core à Azure

Suivez ces étapes pour déployer votre application ASP.NET Core et sa base de données sur Azure.

_Regardez cette vidéo et suivez la procédure pour déployer votre première application ASP.NET Core sur Azure._

> [!VIDEO https://www.youtube.com/embed/n8wz_f5_4wI]

## <a name="open-your-project"></a>Ouvrir votre projet

Ouvrez votre application ASP.NET Core dans Visual Studio 2019. L’application devrait déjà utiliser la configuration avec EF Core et une API web fonctionnelle, suivant la configuration effectuée à [l’étape 4 de cette série de tutoriels](tutorial-aspnet-core-ef-step-04.md).

## <a name="publish-to-azure-app-service"></a>Publier sur Azure App Service

Cliquez avec le bouton droit sur le projet dans l’Explorateur de solutions, puis choisissez **Publier**. Conservez les paramètres par défaut de **App Service** et **Créer**, puis cliquez sur le bouton **Publier**. Si vous ne disposez pas d’un compte Azure, cliquez sur **Créez votre compte Azure gratuit** et suivez la courte procédure d’inscription.

Ajoutez un serveur SQL. Spécifiez un nom d’utilisateur Administrateur et un mot de passe.

![Visual Studio 2019 – Créer un serveur SQL Azure](media/vs-2019/vs2019-azure-sql-server.png)

Ajoutez Application Insights.

Cliquez sur le bouton **Créer** pour continuer.

![Visual Studio 2019 – Créer un service Azure App Service](media/vs-2019/vs2019-azure-create-new-app-service.png)

## <a name="exploring-the-azure-portal-and-your-hosted-app"></a>Explorer le Portail Azure et l’application hébergée

Une fois le service App Service créé, le site se lance dans un navigateur. Pendant son chargement, vous pouvez également accéder au service App Service sur le Portail Azure. Explorez les options disponibles pour votre service App Service : vous y trouverez une section **Vue d’ensemble** permettant de lancer et d’arrêter l’application.

![Options Azure App Service](media/vs-2019/vs2019-azure-app-service-menu-options.png)

### <a name="scalability"></a>Extensibilité

Vous pouvez examiner les options pour mettre l’application à l’échelle ainsi que sur. L’intensification se réfère à l’augmentation des ressources données à chaque instance hébergeant votre application. Avec la montée en charge (scale out), il s’agit d’accroître le nombre d’instances hébergeant l’application. Vous pouvez configurer la mise à l’échelle automatique de votre application, afin d’augmenter automatiquement le nombre d’instances utilisées pour héberger votre application en réponse à une charge, puis de le réduire une fois que la charge a diminué.

### <a name="security-and-compliance"></a>Sécurité et conformité

Le fait d’héberger une application sur Azure présente un autre avantage : la sécurité et la conformité. Azure App Service assure la conformité ISO, SOC et PCI. Nous pouvons choisir d’authentifier les utilisateurs avec Azure Active Directory ou la connexion à des réseaux sociaux comme Twitter, Facebook, Google ou Microsoft. Nous pouvons créer des restrictions d’adresses IP, gérer les identités du service, ajouter des domaines personnalisés et prendre en charge le protocole SSL pour l’application, de même que configurer des sauvegardes avec des copies d’archive restaurables du contenu, de la configuration et de la base de données de l’application. Ces fonctionnalités sont accessibles dans les options de menu Authentification/Autorisation, Identité, Sauvegardes et Paramètres SSL.

### <a name="deployment-slots"></a>Emplacements de déploiement

À l’occasion du déploiement d’une application, il se produit fréquemment un petit temps d’arrêt pendant le redémarrage de l’application. Les emplacements de déploiement évitent ce problème en offrant la possibilité d’effectuer le déploiement sur une instance ou un ensemble d’instances de préproduction distinct, préchauffé avant le passage en production. L’échange consiste simplement en une redirection instantanée et transparente du trafic. S’il se produit des problèmes en production après l’échange, vous pourrez toujours revenir à votre dernier état de production fonctionnel connu.

## <a name="update-connection-string"></a>Mettre à jour la chaîne de connexion

Par défaut, Azure s’attend que la connexion d’une nouvelle application à sa nouvelle base de données SQL Server utilise une chaîne de connexion nommée `DefaultConnection`. L’application que nous avons créée dans cette série de tutoriels a actuellement recours à une chaîne de connexion nommée `AppDbContext`. Nous devons la modifier dans *appsettings.json* et *Startup.cs*, puis redéployer l’application.

## <a name="test-the-app-running-in-azure"></a>Tester l’application en cours d’exécution dans Azure

Accédez au chemin */Games* : vous devriez pouvoir ajouter un nouveau jeu et le voir apparaître. Ensuite, dans le chemin */swagger*, utilisez les points de terminaison d’API web pour vérifier que l’API de l’application fonctionne également.

Félicitations ! Vous avez terminé cette série de tutoriels vidéo.

## <a name="next-steps"></a>Étapes suivantes

Pour savoir comment architecturer des applications ASP.NET Core, consultez ces ressources gratuites.

[Architecture d’application ASP.NET Core](https://dotnet.microsoft.com/learn/web/aspnet-architecture)

## <a name="see-also"></a>Voir aussi

- [Publier une application ASP.NET Core sur Azure avec Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.2)