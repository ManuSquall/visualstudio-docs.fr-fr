---
title: Outils de données Visual Studio pour .NET | Documents Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: b855516e6eb440b970489c3ebc6209dc0573f231
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-data-tools-for-net"></a>Outils de données Visual Studio pour .NET

Visual Studio et .NET Framework constituent une API complète et une prise en charge pour la connexion aux bases de données, modélisation des données en mémoire et afficher les données dans l’interface utilisateur des outils. Les classes .NET Framework qui fournissent des fonctionnalités d’accès aux données sont appelées [ADO.NET](/dotnet/framework/data/adonet/index). ADO.NET, ainsi que les données pour les outils dans Visual Studio, a été conçu principalement pour prendre en charge des bases de données relationnelles et XML. De nos jours, plusieurs fournisseurs de base de données NoSQL ou des tiers offrent des fournisseurs ADO.NET.

[.NET core](/dotnet/core/) prend en charge ADO.NET, à l’exception des jeux de données et les types associés. Si vous ciblez .NET Core et que vous avez besoin d’une couche de mappage relationnel objet (ORM), utilisez [Entity Framework Core](/ef/core/).

Le diagramme suivant montre une vue simplifiée de l’architecture de base :

![Architecture ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png)

Le flux de travail typique est la suivante :

1. Installer un développement ou la base de données de test sur votre ordinateur local. Consultez [l’installation de systèmes de base de données, des outils et des exemples](../data-tools/installing-database-systems-tools-and-samples.md). Si vous utilisez un service de données Azure, cette étape n’est pas nécessaire.

2. Tester la connexion à la base de données (ou service ou fichier local) dans Visual Studio. Consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).

3. (Facultatif) Utilisez les outils pour générer et configurer un nouveau modèle. Modèles basés sur Entity Framework sont la recommandation par défaut pour les nouvelles applications. Le modèle, celle que vous utilisez, est la source de données que l’application interagit avec. Le modèle se trouve logiquement entre la base de données ou de service et de l’application. Consultez [ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md).

4. Faites glisser la source de données à partir de la **des Sources de données** fenêtre sur une aire de conception de Windows Forms, ASP.NET ou Windows Presentation Foundation pour générer le code de liaison de données qui affiche les données à l’utilisateur de la manière que vous spécifiez. Consultez [lier des contrôles aux données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Ajouter du code personnalisé à des éléments tels que les règles d’entreprise, la recherche et la validation des données, ou pour tirer parti des fonctionnalités personnalisées qui expose de la base de données sous-jacente.

Vous pouvez ignorer l’étape 3 et programmer une application .NET pour envoyer des commandes directement à une base de données, au lieu d’utiliser un modèle. Dans ce cas, vous trouverez la documentation correspondante ici : [ADO.NET](/dotnet/framework/data/adonet/index). Notez que vous pouvez toujours utiliser l’Assistant de Configuration de Source de données et les concepteurs pour générer le code de liaison de données lorsque vous remplissez vos propres objets en mémoire, puis de lier des contrôles d’interface utilisateur à ces objets.

## <a name="see-also"></a>Voir aussi

- [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)