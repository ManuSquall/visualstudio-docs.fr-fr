---
title: Data Tools pour .NET
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: 67cf4969a5db8900910b375d4cf560b1e30da4eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281069"
---
# <a name="visual-studio-data-tools-for-net"></a>Outils de données Visual Studio pour .NET

Visual Studio et .NET offrent ensemble une prise en charge étendue des API et des outils pour la connexion aux bases de données, la modélisation des données en mémoire et l’affichage des données dans l’interface utilisateur. Les classes .NET qui fournissent des fonctionnalités d’accès aux données sont appelées [ADO.net](/dotnet/framework/data/adonet/index). ADO.NET, ainsi que les outils de données dans Visual Studio, ont été conçus principalement pour prendre en charge les bases de données relationnelles et XML. Ces jours-là, de nombreux fournisseurs de bases de données NoSQL ou tiers proposent des fournisseurs ADO.NET.

[.Net Core](/dotnet/core/) prend en charge ADO.net, à l’exception des jeux de données et de leurs types associés. Si vous ciblez .NET Core et que vous avez besoin d’une couche de mappage objet/relationnel (ORM), utilisez [Entity Framework Core](/ef/core/).

Le diagramme suivant illustre une vue simplifiée de l’architecture de base :

![Architecture ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Flux de travail classique

Le flux de travail classique est le suivant :

1. Installez une base de données de développement ou de test sur votre ordinateur local. Consultez [installation de systèmes de base de données, d’outils et d’exemples](../data-tools/installing-database-systems-tools-and-samples.md). Si vous utilisez un service de données Azure, cette étape n’est pas nécessaire.

2. Testez la connexion à la base de données (ou au service ou au fichier local) dans Visual Studio. Consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).

3. Facultatif Utilisez les outils pour générer et configurer un nouveau modèle. Les modèles basés sur les Entity Framework sont les recommandations par défaut pour les nouvelles applications. Le modèle, selon celui que vous utilisez, est la source de données avec laquelle l’application interagit. Le modèle se situe logiquement entre la base de données ou le service et l’application. Consultez [ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md).

4. Faites glisser la source de données de la fenêtre **sources de données** vers une aire de conception Windows Forms, ASP.NET ou Windows Presentation Foundation pour générer le code de liaison de données qui affichera les données à l’utilisateur de la manière que vous spécifiez. Consultez [lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Ajoutez du code personnalisé pour des opérations telles que les règles d’entreprise, la recherche et la validation des données, ou pour tirer parti des fonctionnalités personnalisées exposées par la base de données sous-jacente.

Vous pouvez ignorer l’étape 3 et programmer une application .NET pour émettre des commandes directement dans une base de données, plutôt que d’utiliser un modèle. Dans ce cas, vous trouverez la documentation pertinente ici : [ADO.NET](/dotnet/framework/data/adonet/index). Notez que vous pouvez toujours utiliser l' **Assistant Configuration de source de données** et les concepteurs pour générer du code de liaison de données lorsque vous remplissez vos propres objets en mémoire, puis liez les contrôles de l’interface utilisateur à ces objets.

## <a name="see-also"></a>Voir aussi

- [Accéder aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
