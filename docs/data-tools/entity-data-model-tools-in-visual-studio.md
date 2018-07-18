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
ms.openlocfilehash: 0b1d98422d9527220b54232d1180ae4b91a28e6b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922986"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Outils Entity Framework dans Visual Studio
Entity Framework est une technologie de mappage relationnel objet qui permet aux développeurs .NET travailler avec des données relationnelles à l’aide des objets spécifiques au domaine. Du coup, ils n’ont plus à écrire une grande partie du code d’accès aux données qu’ils doivent généralement écrire. Entity Framework est le mappage relationnel objet recommandé (ORM) technologie pour les nouvelles applications .NET de modélisation.

Les outils Entity Framework sont conçues pour vous aider à créer des applications Entity Framework (EF). La documentation complète pour Entity Framework est ici : [EF Core et EF 6](/ef/).

Avec les outils Entity Framework, vous pouvez créer un *modèle conceptuel* à partir d’un fichier de base de données sous forme graphique visualiser et modifier le modèle conceptuel. Vous pouvez également commencer par créer graphiquement un modèle conceptuel, puis générer une base de données prenant en charge ce modèle. Dans les deux cas, vous pouvez mettre à jour automatiquement votre modèle lorsque la base de données sous-jacente change et générer automatiquement le code de couche objet pour votre application. La génération de base de données et la génération de code de couche objet sont personnalisables.

Les outils Entity Framework sont installées dans le cadre de la **stockage de données et de traitement** charge de travail dans le programme d’installation Visual Studio. Vous pouvez également installer un composant individuels sous le **SDK, bibliothèques et infrastructures** catégorie.

Voici les outils spécifiques qui composent les outils Entity Framework dans Visual Studio :

-   Vous pouvez utiliser la [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] concepteur** (**Entity Designer**) pour créer visuellement ou modifier des entités, associations, mappages et des relations d’héritage. Le **Entity Designer** génère également [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] ou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] code de couche objet.

-   Vous pouvez utiliser la  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] Assistant** pour générer un modèle conceptuel à partir d’une base de données et ajouter des informations de connexion de base de données à votre application.

-   Vous pouvez utiliser la **Assistant Création de base de données** pour créer un modèle conceptuel tout d’abord, puis créer une base de données qui prend en charge le modèle.

-   Vous pouvez utiliser la **Assistant modèle de mise à jour** pour mettre à jour votre modèle conceptuel, le modèle de stockage et le mappage lorsque les modifications ont été apportées à la base de données sous-jacente.

    > [!NOTE]
    >  À compter de Visual Studio 2010, les outils Entity Framework ne prennent pas charge [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)].

Les outils génèrent ou modifient un fichier .edmx. Ce fichier .edmx contient des informations qui décrivent le modèle conceptuel, le modèle de stockage et les mappages entre eux. Pour plus d’informations, consultez [EDMX](https://msdn.microsoft.com/data/jj650889.aspx).

[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) vous aider à créer des applications qui utilisent le modèle de données d’entité. Les outils power tools peuvent générer un modèle conceptuel, valider un modèle existant, produire des fichiers de code source qui contiennent des classes d’objets basées sur le modèle conceptuel et produire des fichiers de code source qui contiennent des vues que le modèle génère. Pour plus d’informations, consultez [Pre-Generated des vues de mappage](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index)|Décrit comment utiliser [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] outils, qui [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] fournit, pour créer des applications.|
|[Entity Data Model](/dotnet/framework/data/adonet/entity-data-model)|Fournit des liens et des informations sur l’utilisation des données qui sont utilisées par les applications basées sur [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)].|
|[Entity Framework (EF) Documentation)](https://msdn.microsoft.com/library/ee712907(v=vs.113).aspx)|Fournit un index de vidéos, didacticiels et la documentation avancée pour vous aider à tirer le meilleur parti d’Entity Framework.|
|[ASP.NET 5 Application vers la nouvelle base de données](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Décrit comment créer une nouvelle application ASP.NET 5 à l’aide d’Entity Framework 7.|

## <a name="see-also"></a>Voir aussi

- [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)