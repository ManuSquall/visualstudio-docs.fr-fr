---
title: Outils de données Visual Studio pour .NET | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 841311af90ddf4bedfb9d055e5764068cdc71632
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859705"
---
# <a name="visual-studio-data-tools-for-net"></a>Outils de données Visual Studio pour .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio et .NET Framework fournissent une API complète et une prise en charge pour la connexion aux bases de données, modélisation des données en mémoire et afficher les données dans l’interface utilisateur des outils.  Les classes .NET Framework qui fournissent des fonctionnalités d’accès aux données sont appelées [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). ADO.NET, ainsi que les données des outils dans Visual Studio, a été conçu principalement pour prendre en charge de bases de données relationnelles et XML. De nos jours, de nombreux fournisseurs de base de données NoSQL ou à des tiers, offrent fournisseurs ADO.NET.  
  
 Visual Studio 2015 Update 2 inclut les dernières mises à jour de [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx), qui permettent la prise en charge des fonctionnalités plus récentes dans Azure [base de données SQL](https://azure.microsoft.com/en-us/services/sql-database/) et [SQL Server 2016](https://www.microsoft.com/en-us/server-cloud/products/sql-server-2016/). [.NET core](https://www.dotnetfoundation.org/netcore) prend en charge ADO.NET, à l’exception des jeux de données et les types associés. Si vous ciblez .NET Core et que vous avez besoin d’une couche de mappage objet-relationnel (ORM), utilisez [Entity Framework Core](https://msdn.microsoft.com/data/ef.aspx).  
  
 Le diagramme suivant montre une vue simplifiée de l’architecture de base :  
  
 ![Architecture ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png "raddata diagramme d’Architecture ADO.NET")  
  
 Le flux de travail typique est la suivante :  
  
1. Installer un développement ou la base de données de test sur votre ordinateur local. Consultez [l’installation de systèmes de base de données, des outils et des exemples](../data-tools/installing-database-systems-tools-and-samples.md). Si vous utilisez un service de données Azure, cette étape n’est pas nécessaire.  
  
2. Tester la connexion à la base de données (ou service ou fichier local) dans Visual Studio. Consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).  
  
3. (Facultatif) Utiliser les outils pour générer et configurer un nouveau modèle. Modèles basés sur Entity Framework sont la recommandation par défaut pour les nouvelles applications. Le modèle, celui que vous utilisez, est la source de données que l’application interagit avec. Le modèle se trouve logiquement entre la base de données ou de service et de l’application.  Consultez [ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md).  
  
4. Faites glisser la source de données à partir de la **des Sources de données** fenêtre sur une aire de conception de Windows Forms, ASP.NET ou Windows Presentation Foundation pour générer le code de liaison de données qui affiche les données à l’utilisateur de la façon que vous spécifiez. Consultez [lier des contrôles aux données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
5. Ajouter du code personnalisé pour des éléments tels que les règles d’entreprise, la recherche et la validation des données, ou pour tirer parti des fonctionnalités personnalisées qui expose la base de données sous-jacente.  
  
   Vous pouvez ignorer l’étape 3 et programmer une application .NET pour émettre des commandes directement à une base de données au lieu d’un modèle. Dans ce cas, vous trouverez la documentation pertinente ici : [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). Notez que vous toujours pouvez utiliser l’Assistant de Configuration de Source de données et les concepteurs pour générer le code de liaison de données lorsque vous renseignez vos propres objets en mémoire, puis liez les contrôles d’interface utilisateur à ces objets.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Créer une application de données simple à l’aide d’ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md)  
  
-   [Ajouter de nouvelles connexions](../data-tools/add-new-connections.md)  
  
-   [Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md)  
  
-   [Outils Entity Data Model dans Visual Studio](../data-tools/entity-data-model-tools-in-visual-studio.md)  
  
-   [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
  
-   [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)  
  
-   [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
  
-   [Ressources supplémentaires pour le dépannage des erreurs d’accès aux données](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
-   [Services Windows Communication Foundation et services de données WCF dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)  
  
-   [Création et gestion de bases de données et d’applications de couche Données dans Visual Studio](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)  
  
-   [Ressources supplémentaires pour le dépannage des erreurs d’accès aux données](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)







