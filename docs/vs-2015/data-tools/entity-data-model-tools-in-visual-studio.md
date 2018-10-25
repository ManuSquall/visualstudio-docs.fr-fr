---
title: Entity Data Model Tools dans Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8a3fffb36d7070701b99382c320e3a2d23b9a2b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893401"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>Entity Data Model Tools dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Entity Framework est une technologie de mapping objet-relationnel qui permet aux développeurs .NET de travailler avec des données relationnelles à l’aide des objets spécifiques au domaine. Du coup, ils n’ont plus à écrire une grande partie du code d’accès aux données qu’ils doivent généralement écrire. Entity Framework est le recommandé mappage objet-relationnel (ORM) technologie pour les nouvelles applications .NET de modélisation.  
  
 Depuis mars 2016, la version plus récente est [Entity Framework 6](https://msdn.microsoft.com/data/ef) . [Entity Framework 7](https://docs.efproject.net/en/latest/) est en version préliminaire.  
  
 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Outils sont conçus pour vous aider à créer [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] applications. La documentation complète pour [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Tools est ici : [Entity Framework](https://msdn.microsoft.com/data/jj590134).  
  
 Avec [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] outils, vous pouvez créer un *modèle conceptuel* depuis une base de données puis graphiquement visualiser et modifier votre modèle conceptuel. Vous pouvez également commencer par créer graphiquement un modèle conceptuel, puis générer une base de données prenant en charge ce modèle. Dans les deux cas, vous pouvez mettre à jour automatiquement votre modèle lorsque la base de données sous-jacente change et générer automatiquement le code de couche objet pour votre application. La génération de base de données et la génération de code de couche objet sont personnalisables.  
  
 Voici les outils spécifiques qui composent les Entity Data Model Tools dans Visual Studio 2015 :  
  
- Vous pouvez utiliser la [!INCLUDE[vstecado](../includes/vstecado-md.md)]  **[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] concepteur** (**Entity Designer**) pour créer et modifier des entités, des associations, des mappages et des relations d’héritage visuellement. Le **Entity Designer** génère également [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] ou [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] code de couche objet.  
  
- Vous pouvez utiliser la  **[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Assistant** pour générer un modèle conceptuel à partir d’une base de données existante et ajouter des informations de connexion de base de données à votre application.  
  
- Vous pouvez utiliser la **Assistant Création de la base de données** pour créer un modèle conceptuel tout d’abord, puis créer une base de données qui prend en charge le modèle.  
  
- Vous pouvez utiliser la **Assistant modèle de mise à jour** pour mettre à jour votre modèle conceptuel, le modèle de stockage et le mappage lorsque les modifications ont été apportées à la base de données sous-jacente.  
  
  > [!NOTE]
  >  À partir de Visual Studio 2010, [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] outils ne gèrent pas [!INCLUDE[ss2k](../includes/ss2k-md.md)].  
  
  Les outils génèrent ou modifient un fichier .edmx. Ce fichier contient des informations qui décrivent le modèle conceptuel, le modèle de stockage et les mappages entre eux. Pour plus d’informations, consultez [EDMX](https://msdn.microsoft.com/data/jj650889.aspx).  
  
  Entity Framework Power Tools vous aider à créer des applications qui utilisent l’Entity Data Model. Les outils peuvent générer un modèle conceptuel, valider un modèle existant, produire des fichiers de code source qui contiennent des classes d’objets basées sur le modèle conceptuel et produire des fichiers de code source qui contiennent des vues qui génère le modèle. Pour plus d’informations, consultez [Pre-Generated mappage de vues](https://msdn.microsoft.com/data/dn469601.aspx).  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[ADO.NET Entity Framework](http://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|Décrit comment utiliser [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] outils, qui [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] fournit, pour créer des applications.|  
|[Entity Data Model](http://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|Fournit des liens et des informations sur l’utilisation des données qui sont utilisées par les applications basées [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)].|  
|[Mise en route sur .NET complète (Console, WinForms, WPF, etc.).](https://docs.efproject.net/en/latest/platforms/full-dotnet/getting-started.html)|Fournit des didacticiels sur la façon de créer des applications de bureau .NET qui utilisent Entity Framework 7.|  
|[ASP.NET 5 Application de la nouvelle base de données](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Décrit comment créer une application ASP.NET 5 à l’aide d’Entity Framework 7.|  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)

