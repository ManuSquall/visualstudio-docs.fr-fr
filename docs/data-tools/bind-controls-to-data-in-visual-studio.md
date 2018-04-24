---
title: Lier des contrôles aux données dans Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- dislaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: acb050ebdbbce84eb47e27883c55117a83ddb0c2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Lier des contrôles aux données dans Visual Studio
Vous pouvez afficher des données pour les utilisateurs de votre application en liant des données à des contrôles. Vous pouvez créer ces contrôles liés aux données en faisant glisser des éléments depuis la **des Sources de données** fenêtre sur une aire de conception ou les contrôles sur une aire dans Visual Studio.

 Cette rubrique décrit les sources de données que vous pouvez utiliser pour créer des contrôles liés aux données. Elle décrit également certaines des tâches générales qui entrent en jeu dans la liaison de données. Pour plus d’informations plus spécifiques sur la façon de créer des contrôles liés aux données, consultez [des contrôles de lier des Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) et [WPF de lier des contrôles aux données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

## <a name="data-sources"></a>Sources de données
 Dans le contexte de liaison de données, une source de données représente les données en mémoire qui peut être lié à votre interface utilisateur. En pratique, une source de données peut être une classe Entity Framework, un jeu de données, un point de terminaison de service qui est encapsulé dans un objet de proxy .NET, une classe LINQ to SQL, ou n’importe quel objet .NET ou collection. Certaines sources de données permettent de créer des contrôles liés aux données en faisant glisser des éléments à partir de la **des Sources de données** fenêtre, contrairement à d’autres sources de données. Le tableau suivant affiche les sources de données qui sont prises en charge.

|Source de données|Prise en charge du glisser-déposer dans **le Concepteur Windows Forms**|Prise en charge du glisser-déposer dans **du Concepteur WPF**|Prise en charge du glisser-déposer dans **Concepteur Silverlight**|
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|
|Groupe de données|Oui|Oui|Non|
|Entity Data Model|Oui<sup>1</sup>|Oui|Oui|
|Classes LINQ to SQL|Ne<sup>2</sup>|Ne<sup>2</sup>|Ne<sup>2</sup>|
|Services (y compris [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], WCF services et les services web)|Oui|Oui|Oui|
|Object|Oui|Oui|Oui|
|SharePoint|Oui|Oui|Oui|

 1. Générer le modèle à l’aide de la **Entity Data Model** Assistant, puis faites glisser ces objets vers le concepteur.

 2. Classes LINQ to SQL n’apparaissent pas dans le **des Sources de données** fenêtre. Toutefois, vous pouvez ajouter une nouvelle source de données Objet basée sur les classes LINQ to SQL, puis faire glisser ces objets vers le concepteur pour créer des contrôles liés aux données. Pour plus d’informations, consultez [procédure pas à pas : création de Classes LINQ to SQL (Concepteur O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="data-sources-window"></a>Fenêtre Sources de données
 Sources de données sont disponibles pour votre projet en tant qu’éléments dans le **des Sources de données** fenêtre. Cette fenêtre est visible, ou qu’il est accessible à partir de la **vue** menu, quand une aire de conception du formulaire est la fenêtre active de votre projet. Vous pouvez faire glisser des éléments depuis cette fenêtre pour créer des contrôles liés aux données sous-jacentes, et vous pouvez également configurer les sources de données en cliquant sur.

 ![Fenêtre Sources de données](../data-tools/media/raddata-data-sources-window.png "fenêtre Sources de données de raddata")

 Pour chaque type de données qui s’affiche dans le **des Sources de données** fenêtre, un contrôle par défaut est créé lorsque vous faites glisser l’élément vers le concepteur. Avant de faire glisser un élément à partir de la **des Sources de données** fenêtre, vous pouvez modifier le contrôle qui sera créé. Pour plus d’informations, consultez [définir le contrôle à créer lors du déplacement de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="tasks-involved-in-binding-controls-to-data"></a>Tâches impliquées dans la liaison de contrôles à des données
 Le tableau suivant répertorie certaines des tâches plus courantes que vous effectuez pour lier des contrôles aux données.

|Tâche|Complément d'information|
|----------|----------------------|
|Ouvrez le **des Sources de données** fenêtre.|Ouvrez une aire de conception dans l’éditeur et choisissez **vue** > **des Sources de données**.|
|Ajouter une source de données à votre projet.|[Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md)|
|Définir le contrôle qui est créé lorsque vous faites glisser un élément à partir de la **des Sources de données** fenêtre vers le concepteur.|[Définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|Modifier la liste des contrôles qui sont associés aux éléments dans le **des Sources de données** fenêtre.|[Ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|Créer des contrôles liés aux données.|[Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)|
|Lier à un objet ou une collection.|[Lier des objets dans Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|
|Filtrer les données qui s’affiche dans l’interface utilisateur.|[Guide pratique pour filtrer et trier des données dans une application Windows Forms](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|Personnaliser les légendes pour les contrôles.|[Personnaliser la façon dont Visual Studio crée des légendes pour les contrôles liés aux données](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>Voir aussi

- [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Liaison de données Windows Forms](/dotnet/framework/winforms/windows-forms-data-binding)