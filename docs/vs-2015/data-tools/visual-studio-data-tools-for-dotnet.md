---
title: Outils de données Visual Studio pour .NET | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d591595c65f00e0198ded9492ae0b8399e363e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670097"
---
# <a name="visual-studio-data-tools-for-net"></a>Outils de données Visual Studio pour .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio et le .NET Framework offrent ensemble une prise en charge étendue des API et des outils pour la connexion aux bases de données, la modélisation des données en mémoire et l’affichage des données dans l’interface utilisateur.  Les classes .NET Framework qui fournissent des fonctionnalités d’accès aux données sont appelées [ADO.net](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). ADO.NET, avec les outils de données dans Visual Studio, a été initialement conçu principalement pour prendre en charge les bases de données relationnelles et XML. Ces jours-là, de nombreux fournisseurs de bases de données NoSQL ou tiers proposent des fournisseurs ADO.NET.

 Visual Studio 2015 Update 2 comprend les dernières mises à jour de            [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx), qui permettent la prise en charge des fonctionnalités les plus récentes dans Azure [SQL Database](https://azure.microsoft.com/services/sql-database/) et [SQL Server 2016](https://www.microsoft.com/sql-server/sql-server-2016). [.Net Core](https://www.dotnetfoundation.org/projects?searchquery=dotnet+core&type=project) prend en charge ADO.net, à l’exception des jeux de données et des types associés. Si vous ciblez .NET Core et que vous avez besoin d’une couche de mappage objet/relationnel (ORM), utilisez [Entity Framework Core](https://msdn.microsoft.com/data/ef.aspx).

 Le diagramme suivant illustre une vue simplifiée de l’architecture de base :

 ![Architecture ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png "Diagramme de l’architecture raddata ADO.NET")

 Le flux de travail classique est le suivant :

1. Installez une base de données de développement ou de test sur votre ordinateur local. Consultez [installation de systèmes de base de données, d’outils et d’exemples](../data-tools/installing-database-systems-tools-and-samples.md). Si vous utilisez un service de données Azure, cette étape n’est pas nécessaire.

2. Testez la connexion à la base de données (ou au service ou au fichier local) dans Visual Studio. Consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).

3. Facultatif Utilisez les outils pour générer et configurer un nouveau modèle. Les modèles basés sur les Entity Framework sont les recommandations par défaut pour les nouvelles applications. Le modèle, selon celui que vous utilisez, est la source de données avec laquelle l’application interagit. Le modèle se situe logiquement entre la base de données ou le service et l’application.  Consultez [ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md).

4. Faites glisser la source de données de la fenêtre **sources de données** vers une aire de conception Windows Forms, ASP.NET ou Windows Presentation Foundation pour générer le code de liaison de données qui affichera les données à l’utilisateur de la manière que vous spécifiez. Consultez [lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Ajoutez du code personnalisé pour des opérations telles que les règles d’entreprise, la recherche et la validation des données, ou pour tirer parti des fonctionnalités personnalisées exposées par la base de données sous-jacente.

   Vous pouvez ignorer l’étape 3 et programmer une application .NET pour émettre des commandes directement dans une base de données, plutôt que d’utiliser un modèle. Dans ce cas, vous trouverez la documentation pertinente ici : [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). Notez que vous pouvez toujours utiliser l’Assistant Configuration de source de données et les concepteurs pour générer du code de liaison de données lorsque vous remplissez vos propres objets en mémoire, puis liez les contrôles de l’interface utilisateur à ces objets.

## <a name="in-this-section"></a>Contenu de cette section

- [Créer une application de données simple à l’aide d’ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md)

- [Ajouter de nouvelles connexions](../data-tools/add-new-connections.md)

- [Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md)

- [Entity Data Model Tools dans Visual Studio](../data-tools/entity-data-model-tools-in-visual-studio.md)

- [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)

- [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

- [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

- [Ressources supplémentaires pour le dépannage des erreurs d’accès aux données](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

- [Services Windows Communication Foundation et services de données WCF dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- [Création et gestion de bases de données et d’applications de couche Données dans Visual Studio](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)

- [Ressources supplémentaires pour le dépannage des erreurs d’accès aux données](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

## <a name="see-also"></a>Voir aussi
 [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
