---
title: Outils Entity Framework dans Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 679c91014966167c64296638d9d0a9b2d302d345
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284038"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Outils Entity Framework dans Visual Studio
Entity Framework est une technologie de mapping objet-relationnel qui permet aux développeurs .NET de travailler avec des données relationnelles à l’aide des objets spécifiques au domaine. Du coup, ils n’ont plus à écrire une grande partie du code d’accès aux données qu’ils doivent généralement écrire. Entity Framework est le recommandé mappage objet-relationnel (ORM) technologie pour les nouvelles applications .NET de modélisation.

Outils Entity Framework sont conçues pour vous aider à créer des applications Entity Framework (EF). La documentation complète pour Entity Framework est ici : [EF Core et EF 6](/ef/).

Avec les outils Entity Framework, vous pouvez créer un *modèle conceptuel* depuis une base de données puis graphiquement visualiser et modifier votre modèle conceptuel. Vous pouvez également commencer par créer graphiquement un modèle conceptuel, puis générer une base de données prenant en charge ce modèle. Dans les deux cas, vous pouvez mettre à jour automatiquement votre modèle lorsque la base de données sous-jacente change et générer automatiquement le code de couche objet pour votre application. La génération de base de données et la génération de code de couche objet sont personnalisables.

Les outils Entity Framework sont installés dans le cadre de la **stockage de données et de traitement** charge de travail dans Visual Studio Installer. Vous pouvez également les installer comme composant individuels sous le **SDK, bibliothèques et infrastructures** catégorie.

Voici les outils spécifiques qui composent les outils Entity Framework dans Visual Studio :

-   Vous pouvez utiliser la [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] concepteur** (**Entity Designer**) pour créer et modifier des entités, des associations, des mappages et des relations d’héritage visuellement. Le **Entity Designer** génère également [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] ou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] code de couche objet.

-   Vous pouvez utiliser la  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] Assistant** pour générer un modèle conceptuel à partir d’une base de données existante et ajouter des informations de connexion de base de données à votre application.

-   Vous pouvez utiliser la **Assistant Création de la base de données** pour créer un modèle conceptuel tout d’abord, puis créer une base de données qui prend en charge le modèle.

-   Vous pouvez utiliser la **Assistant modèle de mise à jour** pour mettre à jour votre modèle conceptuel, le modèle de stockage et le mappage lorsque les modifications ont été apportées à la base de données sous-jacente.

    > [!NOTE]
    >  À compter de Visual Studio 2010, les outils Entity Framework ne gèrent pas [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)].

Les outils génèrent ou modifient un *.edmx* fichier. Cela *.edmx* fichier contient des informations qui décrivent le modèle conceptuel, le modèle de stockage et les mappages entre eux. Pour plus d’informations, consultez [EDMX](https://docs.microsoft.com/ef/ef6/).

[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) vous aider à créer des applications qui utilisent l’Entity Data Model. Les power tools peuvent générer un modèle conceptuel, valider un modèle existant, produire des fichiers de code source qui contiennent des classes d’objets basées sur le modèle conceptuel et produisent des fichiers de code source qui contiennent des vues qui génère le modèle. Pour plus d’informations, consultez [Pre-Generated mappage de vues](https://docs.microsoft.com/ef/ef6/fundamentals/performance/pre-generated-views).

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index)|Décrit comment utiliser [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] outils, qui [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] fournit, pour créer des applications.|
|[Entity Data Model](/dotnet/framework/data/adonet/entity-data-model)|Fournit des liens et des informations sur l’utilisation des données qui sont utilisées par les applications basées [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)].|
|[Documentation d’Entity Framework (EF))](https://docs.microsoft.com/ef/ef6/get-started)|Fournit un index des vidéos, didacticiels et documentation avancée pour vous aider à tirer le meilleur parti d’Entity Framework.|
|[ASP.NET 5 Application de la nouvelle base de données](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Décrit comment créer une application ASP.NET 5 à l’aide d’Entity Framework 7.|

## <a name="see-also"></a>Voir aussi

- [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)