---
title: Lier des contrôles à des données
description: Liez des contrôles à des données dans Visual Studio. Créez des contrôles liés aux données en faisant glisser des éléments depuis la fenêtre sources de données.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- displaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1b48c2e8b557a47c1ed795b6f9d3c3ced6247a43
ms.sourcegitcommit: 63ff7cb85b3baeeb713240d17bb2a18497f3741d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94518620"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Lier des contrôles à des données dans Visual Studio

Vous pouvez afficher des données pour les utilisateurs de votre application en liant des données à des contrôles. Vous pouvez créer ces contrôles liés aux données en faisant glisser des éléments depuis la fenêtre **sources de données** vers une aire de conception ou des contrôles sur une surface dans Visual Studio.

Cette rubrique décrit les sources de données que vous pouvez utiliser pour créer des contrôles liés aux données. Elle décrit également certaines des tâches générales qui entrent en jeu dans la liaison de données. Pour plus d’informations sur la façon de créer des contrôles liés aux données, consultez [lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) et [lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

## <a name="data-sources"></a>Sources de données

Dans le contexte de la liaison de données, une source de données représente les données en mémoire qui peuvent être liées à votre interface utilisateur. En pratique, une source de données peut être une classe Entity Framework, un DataSet, un point de terminaison de service encapsulé dans un objet proxy .NET, une classe LINQ to SQL ou n’importe quel objet ou collection .NET. Certaines sources de données vous permettent de créer des contrôles liés aux données en faisant glisser des éléments de la fenêtre **Sources de données** , contrairement à d’autres sources de données. Le tableau suivant affiche les sources de données qui sont prises en charge.

| Source de données | Prise en charge du glisser-déplacer dans le **Concepteur Windows Forms** | Prise en charge du glisser-déplacer dans le **Concepteur WPF** | Prise en charge du glisser-déplacer dans le **Concepteur Silverlight** |
| - | - | - | - |
| Dataset | Oui | Oui | Non |
| Entity Data Model | Oui<sup>1</sup> | Oui | Oui |
| Classes LINQ to SQL | Non <sup>2</sup> | Non <sup>2</sup> | Non <sup>2</sup> |
| Services (notamment [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], les services WCF et les services web) | Oui | Oui | Oui |
| Object | Oui | Oui | Oui |
| SharePoint | Oui | Oui | Oui |

1. Générez le modèle à l’aide de l’Assistant **Entity Data Model** , puis faites glisser ces objets vers le concepteur.

2. Les classes LINQ to SQL ne s’affichent pas dans la fenêtre **Sources de données**. Toutefois, vous pouvez ajouter une nouvelle source de données Objet basée sur les classes LINQ to SQL, puis faire glisser ces objets vers le concepteur pour créer des contrôles liés aux données. Pour plus d’informations, consultez [procédure pas à pas : création de Classes LINQ to SQL (Concepteur O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="data-sources-window"></a>Fenêtre Sources de données

Les sources de données peuvent être utilisées par votre projet sous la forme d’éléments dans la fenêtre **Sources de données**. Cette fenêtre est visible quand une aire de conception de formulaire est la fenêtre active dans votre projet, ou vous pouvez l’ouvrir (quand un projet est ouvert) en choisissant **Afficher** d'  >  **autres**  >  **sources de données** Windows. Vous pouvez faire glisser des éléments à partir de cette fenêtre pour créer des contrôles liés aux données sous-jacentes, et vous pouvez également configurer les sources de données en cliquant avec le bouton droit.

![Fenêtre Sources de données](../data-tools/media/raddata-data-sources-window.png)

Pour chaque type de données qui apparaît dans la fenêtre **Sources de données** , un contrôle par défaut est créé quand vous faites glisser l’élément vers le concepteur. Avant de faire glisser un élément de la fenêtre **sources de données** , vous pouvez modifier le contrôle qui est créé. Pour plus d’informations, consultez [définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="tasks-involved-in-binding-controls-to-data"></a>Tâches impliquées dans la liaison de contrôles à des données

Le tableau suivant répertorie certaines des tâches les plus courantes que vous effectuez pour lier des contrôles à des données.

|Tâche|Plus d’informations|
|----------| - |
|Ouvrez la fenêtre **Sources de données**.|Ouvrez une aire de conception dans l’éditeur, puis choisissez **Afficher** les  >  **sources de données**.|
|Ajoutez une source de données à votre projet.|[Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md)|
|Définissez le contrôle créé lorsque vous faites glisser un élément de la fenêtre **Sources de données** vers le concepteur.|[Définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|Modifiez la liste des contrôles associés aux éléments dans la fenêtre **Sources de données**.|[Ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|Créer des contrôles liés aux données.|[Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)|
|Lier à un objet ou une collection.|[Lier des objets dans Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|
|Filtrer les données qui s’affichent dans l’interface utilisateur.|[Filtrer et trier des données dans une application Windows Forms](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|Personnaliser les légendes pour les contrôles.|[Personnaliser la façon dont Visual Studio crée des légendes pour les contrôles liés aux données](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>Voir aussi

- [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Liaison de données Windows Forms](/dotnet/framework/winforms/windows-forms-data-binding)
