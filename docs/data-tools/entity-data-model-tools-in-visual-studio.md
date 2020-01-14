---
title: Outils Entity Framework
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 250f1ad55f8d60396b8423098e58801d0ed81e77
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916735"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Entity Framework Tools dans Visual Studio

Entity Framework est une technologie de mappage relationnel objet qui permet aux développeurs .NET de travailler avec des données relationnelles à l’aide d’objets spécifiques au domaine. Du coup, ils n’ont plus à écrire une grande partie du code d’accès aux données qu’ils doivent généralement écrire. Entity Framework est la technologie de modélisation ORM (Object-Relational Mapping) recommandée pour les nouvelles applications .NET.

Entity Framework Tools sont conçus pour vous aider à générer des applications Entity Framework (EF). La documentation complète de Entity Framework est disponible ici : [vue d’ensemble-EF 6](/ef/ef6/).

  > [!NOTE]
  > Le Entity Framework Tools décrit dans cette page est utilisé pour générer des fichiers *. edmx* , qui ne sont pas pris en charge dans les EF Core. Pour générer un modèle de EF Core à partir d’une base de données existante, consultez [ingénierie inverse-EF Core](/ef/core/managing-schemas/scaffolding). Pour plus d’informations sur les différences entre EF 6 et EF Core, consultez la section [compare EF 6 et EF Core](/ef/efcore-and-ef6/).

Avec Entity Framework Tools, vous pouvez créer un *modèle conceptuel* à partir d’une base de données existante, puis visualiser et modifier graphiquement votre modèle conceptuel. Vous pouvez également commencer par créer graphiquement un modèle conceptuel, puis générer une base de données prenant en charge ce modèle. Dans les deux cas, vous pouvez mettre à jour automatiquement votre modèle lorsque la base de données sous-jacente change et générer automatiquement le code de couche objet pour votre application. La génération de base de données et la génération de code de couche objet sont personnalisables.

Les outils de Entity Framework sont installés dans le cadre de la charge de travail **stockage et traitement des données** dans le Visual Studio installer. Vous pouvez également les installer en tant que composant individuel sous la catégorie **Kits de développement logiciel (SDK), bibliothèques et infrastructures** .

Il s’agit des outils spécifiques qui composent Entity Framework Tools dans Visual Studio :

- Vous pouvez utiliser le **Concepteur de[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]** [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] (**Entity designer**) pour créer et modifier visuellement des entités, des associations, des mappages et des relations d’héritage. Le **Entity designer** génère également [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] ou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] code de couche objet.

- Vous pouvez utiliser l' **assistant[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]** pour générer un modèle conceptuel à partir d’une base de données existante et ajouter des informations de connexion de base de données à votre application.

- Vous pouvez utiliser l' **Assistant Création** d’une base de données pour créer d’abord un modèle conceptuel, puis créer une base de données qui prend en charge le modèle.

- Vous pouvez utiliser l' **Assistant Mise à jour du modèle** pour mettre à jour votre modèle conceptuel, le modèle de stockage et les mappages lorsque des modifications ont été apportées à la base de données sous-jacente.

  > [!NOTE]
  > À compter de Visual Studio 2010, les outils de Entity Framework ne prennent pas en charge [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)].

Les outils génèrent ou modifient un fichier *. edmx* . Ce fichier *. edmx* contient des informations qui décrivent le modèle conceptuel, le modèle de stockage et les mappages entre eux. Pour plus d’informations, consultez [edmx](/ef/ef6/).

[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) vous aide à créer des applications qui utilisent le Entity Data Model. Les outils Power Tools peuvent générer un modèle conceptuel, valider un modèle existant, produire des fichiers de code source qui contiennent des classes d’objets basées sur le modèle conceptuel et produire des fichiers de code source qui contiennent des vues générées par le modèle. Pour plus d’informations, consultez [vues de mappage prégénérées](/ef/ef6/fundamentals/performance/pre-generated-views).

## <a name="related-topics"></a>Rubriques connexes

| Titre | Description |
| - | - |
| [ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index) | Décrit comment utiliser les outils de [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)], que [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] fournit, pour créer des applications. |
| [Entity Data Model](/dotnet/framework/data/adonet/entity-data-model) | Fournit des liens et des informations sur l’utilisation des données utilisées par les applications basées sur [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]. |
| [Documentation Entity Framework (EF))](/ef/ef6/get-started) | Fournit un index des vidéos, des didacticiels et une documentation avancée pour vous aider à tirer le meilleur parti de Entity Framework. |
| [Application ASP.NET 5 à une nouvelle base de données](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html) | Décrit comment créer une nouvelle application ASP.NET 5 à l’aide de Entity Framework 7. |

## <a name="see-also"></a>Voir aussi

- [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
