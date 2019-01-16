---
title: Outils de données pour .NET
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: 24da256ac835e477465845714cc844ac5bb305d7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872750"
---
# <a name="visual-studio-data-tools-for-net"></a>Outils de données Visual Studio pour .NET

Visual Studio et .NET Framework fournissent une API complète et une prise en charge pour la connexion aux bases de données, modélisation des données en mémoire et afficher les données dans l’interface utilisateur des outils. Les classes .NET Framework qui fournissent des fonctionnalités d’accès aux données sont appelées [ADO.NET](/dotnet/framework/data/adonet/index). ADO.NET, ainsi que les données des outils dans Visual Studio, a été principalement conçu pour prendre en charge des bases de données relationnelles et XML. De nos jours, de nombreux fournisseurs de base de données NoSQL ou à des tiers, offrent fournisseurs ADO.NET.

[.NET core](/dotnet/core/) prend en charge ADO.NET, à l’exception des jeux de données et les types associés. Si vous ciblez .NET Core et que vous avez besoin d’une couche de mappage objet-relationnel (ORM), utilisez [Entity Framework Core](/ef/core/).

Le diagramme suivant montre une vue simplifiée de l’architecture de base :

![Architecture ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Flux de travail classique

Le flux de travail typique est la suivante :

1. Installer un développement ou la base de données de test sur votre ordinateur local. Consultez [l’installation de systèmes de base de données, des outils et des exemples](../data-tools/installing-database-systems-tools-and-samples.md). Si vous utilisez un service de données Azure, cette étape n’est pas nécessaire.

2. Tester la connexion à la base de données (ou service ou fichier local) dans Visual Studio. Consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).

3. (Facultatif) Utiliser les outils pour générer et configurer un nouveau modèle. Modèles basés sur Entity Framework sont la recommandation par défaut pour les nouvelles applications. Le modèle, celui que vous utilisez, est la source de données avec lequel l’application interagit. Le modèle se trouve logiquement entre la base de données ou de service et de l’application. Consultez [ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md).

4. Faites glisser la source de données à partir de la **des Sources de données** fenêtre sur une aire de conception de Windows Forms, ASP.NET ou Windows Presentation Foundation pour générer le code de liaison de données qui affiche les données à l’utilisateur de la façon que vous spécifiez. Consultez [lier des contrôles aux données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Ajouter du code personnalisé pour des éléments tels que les règles d’entreprise, la recherche et la validation des données, ou pour tirer parti des fonctionnalités personnalisées qui expose la base de données sous-jacente.

Vous pouvez ignorer l’étape 3 et programmer une application .NET pour émettre des commandes directement à une base de données au lieu d’un modèle. Dans ce cas, vous trouverez la documentation pertinente ici : [ADO.NET](/dotnet/framework/data/adonet/index). Notez que vous pouvez utiliser la **Assistant de Configuration de Source de données** et les concepteurs pour générer le code de liaison de données lorsque vous renseignez vos propres objets en mémoire, puis liez les contrôles d’interface utilisateur à ces objets.

## <a name="see-also"></a>Voir aussi

- [Accéder aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)