---
title: Entity Data Model Tools
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d663b86603145f8a665f189e5abfbfa2b0b360ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672393"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>Entity Data Model Tools dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Entity Framework est une technologie de mappage relationnel objet qui permet aux développeurs .NET de travailler avec des données relationnelles à l’aide d’objets spécifiques au domaine. Il élimine le recours à la plupart du code d’accès aux données que les développeurs doivent généralement écrire. Entity Framework est la technologie de modélisation ORM (Object-Relational Mapping) recommandée pour les nouvelles applications .NET.

 Depuis le 2016 mars, la version finale la plus récente est [Entity Framework 6](https://msdn.microsoft.com/data/ef) . [Entity Framework 7](https://docs.efproject.net/en/latest/) est en version préliminaire.

 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Les outils sont conçus pour vous aider à créer des [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] applications. La documentation complète pour les [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] outils est disponible ici : [Entity Framework](https://msdn.microsoft.com/data/jj590134).

 Avec les [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Outils, vous pouvez créer un *modèle conceptuel* à partir d’une base de données existante, puis visualiser et modifier graphiquement votre modèle conceptuel. Vous pouvez également commencer par créer graphiquement un modèle conceptuel, puis générer une base de données prenant en charge ce modèle. Dans les deux cas, vous pouvez mettre à jour automatiquement votre modèle lorsque la base de données sous-jacente change et générer automatiquement le code de couche objet pour votre application. La génération de base de données et la génération de code de couche objet sont personnalisables.

 Il s’agit des outils spécifiques qui composent Entity Data Model Tools dans Visual Studio 2015 :

- Vous pouvez utiliser le [!INCLUDE[vstecado](../includes/vstecado-md.md)] ** [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Concepteur** (**Entity designer**) pour créer et modifier visuellement des entités, des associations, des mappages et des relations d’héritage. Le **Entity designer** génère également [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] un code de couche objet ou.

- Vous pouvez utiliser l' ** [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Assistant** pour générer un modèle conceptuel à partir d’une base de données existante et ajouter des informations de connexion de base de données à votre application.

- Vous pouvez utiliser l' **Assistant Création** d’une base de données pour créer d’abord un modèle conceptuel, puis créer une base de données qui prend en charge le modèle.

- Vous pouvez utiliser l' **Assistant Mise à jour du modèle** pour mettre à jour votre modèle conceptuel, le modèle de stockage et les mappages lorsque des modifications ont été apportées à la base de données sous-jacente.

  > [!NOTE]
  > À compter de Visual Studio 2010, les [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] outils ne prennent pas en charge [!INCLUDE[ss2k](../includes/ss2k-md.md)] .

  Les outils génèrent ou modifient un fichier. edmx. Ce fichier contient des informations qui décrivent le modèle conceptuel, le modèle de stockage et les mappages entre eux. Pour plus d’informations, consultez  [edmx](https://msdn.microsoft.com/data/jj650889.aspx).

  Entity Framework Power Tools vous aide à créer des applications qui utilisent le Entity Data Model. Les outils peuvent générer un modèle conceptuel, valider un modèle existant, produire des fichiers de code source qui contiennent des classes d’objets basées sur le modèle conceptuel et produire des fichiers de code source qui contiennent des vues générées par le modèle. Pour plus d’informations, consultez [vues de mappage prégénérées](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[ADO.NET Entity Framework](https://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|Décrit comment utiliser [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] les outils, qui [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] fournissent, pour créer des applications.|
|[Entity Data Model](https://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|Fournit des liens et des informations sur l’utilisation des données utilisées par les applications basées sur [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] .|
|[Prise en main sur .NET complet (console, WinForms, WPF, etc.)](/ef/ef6/get-started)|Fournit des didacticiels sur la façon de créer des applications de bureau .NET qui utilisent Entity Framework 7.|
|[Application ASP.NET 5 à une nouvelle base de données](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Décrit comment créer une nouvelle application ASP.NET 5 à l’aide de Entity Framework 7.|

## <a name="see-also"></a>Voir aussi
 [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
