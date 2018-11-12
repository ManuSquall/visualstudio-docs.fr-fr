---
title: Comment migrer et publier une Application Web à un Service Cloud Azure depuis Visual Studio | Microsoft Docs
description: Apprenez à migrer et publier votre application web à un service cloud Azure à l’aide de Visual Studio
author: ghogen
manager: douge
ms.assetid: 9394adfd-a645-4664-9354-dd5df08e8c91
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: c122b54a4e22285678d13213cc73d6492baba629
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002067"
---
# <a name="how-to-migrate-and-publish-a-web-application-to-an-azure-cloud-service-from-visual-studio"></a>Comment : migrer et publier une Application Web à un Service Cloud Azure à partir de Visual Studio

Pour tirer parti des services d’hébergement et l’extensibilité d’Azure, vous souhaiterez peut-être migrer et déployer votre application web à un service cloud Azure. Uniquement des modifications minimales sont requises. Cet article couvre le déploiement dans les services de cloud uniquement ; pour App Service, consultez [déployer une application web dans Azure App Service](/azure/app-service/app-service-deploy-local-git).

> [!Important]
> Cette migration est prise en charge uniquement pour les projets ASP.NET, Silverlight, WCF et WCF Workflow spécifiques. Il n’est pas pris en charge pour les projets ASP.NET Core. Consultez [pris en charge les modèles de projet](#supported-project-templates).

## <a name="migrate-a-project-to-cloud-services"></a>Migrer un projet de services cloud

1. Cliquez sur le projet d’application web et sélectionnez **convertir > Convertir en projet Microsoft Azure Cloud Service**. (Notez que cette commande n’apparaît pas si vous avez déjà un projet de rôle web dans la solution).
1. Visual Studio crée un projet de service cloud dans la solution qui contient le rôle web nécessaire. Le nom de ce projet est le même que votre projet d’application avec le suffixe `.Azure`.
1. Visual Studio définit également la **copie locale** propriété sur true pour tous les assemblys qui sont nécessaires pour MVC 2, MVC 3, MVC 4 et Silverlight Business Applications. Cette propriété ajoute ces assemblys au package de services qui est utilisé pour le déploiement.

   > [!Important]
   > Si vous avez d’autres assemblys ou les fichiers qui sont requis pour cette application web, vous devez définir manuellement les propriétés de ces fichiers. Pour plus d’informations sur la façon de définir ces propriétés, consultez [inclure des fichiers dans le Package de Service](#include-files-in-the-service-package).

### <a name="errors-and-warnings"></a>Erreurs et avertissements

Les avertissements ou erreurs qui se produisent indiquent des problèmes à résoudre avant de déployer vers Azure, tels que des assemblys manquants.

Si vous générez votre application, exécutez localement à l’aide de l’émulateur de calcul ou publiez sur Azure, vous pouvez voir l’erreur : « le chemin d’accès spécifié, le nom de fichier ou les deux sont trop longs ». Cette erreur indique que la longueur du nom qualifié complet du projet Azure dépasse 146 caractères. Pour corriger le problème, déplacez votre solution vers un autre dossier avec un chemin plus court.

Pour plus d’informations sur la façon de traiter tous les avertissements comme des erreurs, consultez [configurer un projet de Service Cloud Azure avec Visual Studio](vs-azure-tools-configuring-an-azure-project.md).

### <a name="test-the-migration-locally"></a>Tester localement la migration

1. Dans Visual Studio **l’Explorateur de solutions**, cliquez sur le projet de service cloud ajouté et sélectionnez **définir comme projet de démarrage**.
1. Sélectionnez **Déboguer > Démarrer le débogage** (F5) pour lancer l’environnement de débogage Azure. Cet environnement fournit spécifiquement l’émulation des divers services Azure.

### <a name="use-an-azure-sql-database-for-your-application"></a>Utiliser une base de données SQL Azure pour votre application

Si vous avez une chaîne de connexion pour votre application web qui utilise une base de données SQL Server en local, vous devez migrer votre base de données à base de données SQL Azure au lieu de cela et mettre à jour votre chaîne de connexion. Pour obtenir des conseils avec ce processus, consultez les rubriques suivantes :

- [Migration de base de données SQL Server vers SQL Database dans le cloud](/azure/sql-database/sql-database-cloud-migrate)
- [Utilisation de .NET (C#) avec Visual Studio pour vous connecter et interroger et de la base de données SQL Azure](/azure/sql-database/sql-database-connect-query-dotnet-visual-studio).

## <a name="publish-the-application-to-azure-cloud-service"></a>Publier l’application dans Azure Cloud Service

1. Créer le cloud nécessaire comptes de stockage et de service dans votre abonnement Azure comme décrit sur [préparer la publication ou le déploiement d’une application Azure à partir de Visual Studio](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md).
1. Dans Visual Studio, cliquez sur le projet d’application et sélectionnez **publier sur Microsoft Azure...**  (qui est différent de la commande « Publier … ».).
1. Dans le **publier l’Application Azure** qui apparaît, connectez-vous à l’aide du compte avec votre abonnement Azure et sélectionnez **suivant >**.
1. Dans le **Paramètres > Paramètres communs** , sélectionnez le service de cloud cible à partir de la **Service Cloud** la liste déroulante, ainsi que votre environnement sélectionné et les configurations. 
1. Dans **Paramètres > Paramètres avancés**, sélectionnez le compte de stockage à utiliser, puis sélectionnez **suivant >**.
1. Dans **Diagnostics**, choisissez s’il faut envoyer des informations à Application Insights.
1. Sélectionnez **suivant >** pour afficher un résumé, puis sélectionnez **publier** pour démarrer le déploiement.
1. Visual Studio ouvre une fenêtre de journal d’activité dans laquelle vous pouvez suivre la progression :

    ![VST_AzureActivityLog](./media/vs-azure-tools-migrate-publish-web-app-to-cloud-service/IC744149.png)

1. (Facultatif) Pour annuler le processus de déploiement, cliquez sur l’élément de ligne dans le journal d’activité et choisissez **Annuler et supprimer**. Cette commande arrête le processus de déploiement et supprime l’environnement de déploiement d’Azure. Remarque : pour supprimer cet environnement de déploiement après qu’il a été déployé, vous devez utiliser le [Azure portal](https://portal.azure.com).
1. (Facultatif) Après avoir démarré vos instances de rôle, Visual Studio affiche automatiquement l’environnement de déploiement dans le **Explorateur de serveurs > Services Cloud** nœud. À partir de là, vous pouvez afficher l’état de chaque instance de rôle.
1. Pour accéder à votre application après le déploiement, cliquez sur la flèche en regard de votre déploiement quand le statut **terminé** s’affiche dans le **journal des activités Azure** avec l’URL. Consultez le tableau suivant pour plus d’informations sur le démarrage d’un type spécifique de l’application web à partir d’Azure.

## <a name="using-the-compute-emulator-and-starting-application-in-azure"></a>À l’aide de l’émulateur de calcul et le démarrage d’application dans Azure

Tous les types d’applications peuvent être démarrées dans un navigateur connecté au débogueur Visual Studio en sélectionnant **Déboguer > Démarrer le débogage** (F5). Avec un projet d’Application Web ASP.NET vide, vous devez d’abord ajouter un `.aspx` page dans votre application et le définir comme page de démarrage pour votre projet web.

Le tableau suivant fournit des détails sur le démarrage de l’application dans Azure :

   | Type d’Application Web | En cours d’exécution dans Azure |
   | --- | --- | --- |
   | Application web ASP.NET<br/>(y compris MVC 2, MVC 3, MVC 4) | Sélectionnez l’URL dans le **déploiement** onglet pour le **journal des activités Azure**. |
   | Application Web ASP.NET vide | Si vous avez une valeur par défaut `.aspx` dans votre application, sélectionnez l’URL dans le **déploiement** onglet pour le **journal des activités Azure**. Pour accéder à une autre page, entrez une URL sous la forme suivante dans un navigateur : `<deployment_url>/<page_name>.aspx` |
   | Application Silverlight<br/>Application métier Silverlight<br/>Application de Navigation Silverlight | Accédez à la page spécifique de votre application en utilisant le format d’URL suivant : `<deployment_url>/<page_name>.aspx` |
    Application de service WCF<br/>Application de service de workflow WCF | Définir le `.svc` fichier en tant que la page de démarrage pour votre projet de Service WCF. Puis accédez à `<deployment_url>/<service_file>.svc` |
   | ASP.NET Dynamic Entities<br/>Dynamic Data ASP.NET Linq to SQL | Mettre à jour la chaîne de connexion comme décrit dans la section suivante. Puis accédez à `<deployment_url>/<page_name>.aspx`. Pour Linq to SQL, vous devez utiliser une base de données SQL Azure. |

## <a name="update-a-connection-string-for-aspnet-dynamic-entities"></a>Mettre à jour une chaîne de connexion pour ASP.NET Dynamic Entities

1. Créez une base de données SQL Azure pour une application web de ASP.NET Dynamic Entities comme décrit précédemment dans (#use-an-azuresql-database-for-your-application).
1. Ajoutez les tables et les champs dont vous avez besoin pour cette base de données à partir du portail Azure.
1. Spécifiez une chaîne de connexion dans le `web.config` de fichiers avec le format suivant et enregistrez le fichier :

    ```xml
    <addname="tempdbEntities"connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;data source=<server name>\SQLEXPRESS;initial catalog=<database name>;integrated security=True;multipleactiveresultsets=True;App=EntityFramework&quot;"providerName="System.Data.EntityClient"/>
    ```

    Mise à jour le *connectionString* valeur avec la chaîne de connexion ADO.NET pour votre base de données SQL Azure comme suit :

    ```xml
    XMLCopy<addname="tempdbEntities"connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;Server=tcp:<SQL Azure server name>.database.windows.net,1433;Database=<database name>;User ID=<user name>;Password=<password>;Trusted_Connection=False;Encrypt=True;multipleactiveresultsets=True;App=EntityFramework&quot;"providerName="System.Data.EntityClient"/>
    ```

## <a name="supported-project-templates"></a>Modèles de projet pris en charge

Les applications qui peuvent être migrées et publiées dans les services de cloud doivent utiliser un des modèles dans le tableau ci-dessous. ASP.NET Core n’est pas pris en charge.

| Groupe de modèles | Modèle de projet |
| --- | --- |
| Web | Application Web ASP.NET (.NET Framework) |
| Web | Application Web ASP.NET MVC 2 |
| Web | Application Web ASP.NET MVC 3 |
| Web | Application Web de ASP.NET MVC 4 |
| Web | Application Web ASP.NET vide (ou Site) |
| Web | Application de site Web vide ASP.NET MVC 2 |
| Web | Application Web ASP.NET Dynamic Data Entities |
| Web | ASP.NET Dynamic Data Linq to SQL Web Application |
| Silverlight | Application Silverlight |
| Silverlight | Application métier Silverlight |
| Silverlight | Application de Navigation Silverlight |
| WCF | Application de service WCF |
| WCF | Application de service de workflow WCF |
| Flux de travail | Application de service de workflow WCF |

## <a name="next-steps"></a>Étapes suivantes

- [Préparer la publication ou le déploiement d’une Application Azure à partir de Visual Studio](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)
- [Configuration des informations d’authentification nommées](vs-azure-tools-setting-up-named-authentication-credentials.md).
