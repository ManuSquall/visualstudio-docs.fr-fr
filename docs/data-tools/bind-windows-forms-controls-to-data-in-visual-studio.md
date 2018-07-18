---
title: Lier des contrôles Windows Forms à des données dans Visual Studio
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4652d8dd3e9be582bc15c4644711accc06fd283f
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845520"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Lier des contrôles Windows Forms à des données dans Visual Studio
Vous pouvez afficher des données aux utilisateurs de votre application en liant des données à des Windows Forms. Pour créer ces contrôles liés aux données, faites glisser des éléments à partir de la **des Sources de données** fenêtre jusqu’au Concepteur Windows Forms dans Visual Studio.

![Opération de glisser de Source de données](../data-tools/media/raddata-data-source-drag-operation.png)

Avant de faire glisser des éléments, vous pouvez définir le type de contrôle que vous souhaitez établir une liaison. Des valeurs différentes s’affichent selon que vous choisissez la table elle-même, ou une colonne individuelle.  Vous pouvez également définir des valeurs personnalisées. Pour une table, **détails** signifie que chaque colonne est liée à un contrôle séparé.

![Lier la source de données à un DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>Contrôles BindingSource et BindingNavigator
Le composant <xref:System.Windows.Forms.BindingSource> remplit deux fonctions. Tout d’abord, il fournit une couche d’abstraction lors de la liaison des contrôles aux données. Contrôles du formulaire sont liés à la <xref:System.Windows.Forms.BindingSource> composant au lieu de directement à une source de données. Deuxièmement, il peut gérer une collection d’objets. Ajout d’un type à la <xref:System.Windows.Forms.BindingSource> crée une liste de ce type.

Pour plus d’informations sur le <xref:System.Windows.Forms.BindingSource> composant, consultez :

-   [Composant BindingSource](/dotnet/framework/winforms/controls/bindingsource-component)

-   [Vue d’ensemble du composant BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)

-   [Architecture du composant BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

Le [contrôle BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) fournit une interface utilisateur pour parcourir les données affichées par une application Windows.

## <a name="bind-to-data-in-a-datagridview-control"></a>Lier à des données dans un contrôle DataGridView
Pour un [contrôle DataGridView](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), la table entière est liée à ce contrôle unique. Lorsque vous faites glisser un **DataGridView** au formulaire, un outil de la frange pour parcourir les enregistrements (<xref:System.Windows.Forms.BindingNavigator>) s’affiche également. Un [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état du composant. Dans l’illustration suivante, un [TableAdapterManager](https://msdn.microsoft.com/library/bb384426.aspx) est également ajouté, car la table Customers a une relation avec la table Orders. Ces variables sont déclarées dans le code généré automatiquement en tant que membres privés dans la classe de formulaire. Le code généré automatiquement pour remplir le **DataGridView** se trouve dans le `Form_Load` Gestionnaire d’événements. Le code pour enregistrer les données pour mettre à jour de la base de données se trouve dans le `Save` Gestionnaire d’événements pour le **BindingNavigator**. Vous pouvez déplacer ou modifier ce code en fonction des besoins.

![GridView avec BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

Vous pouvez personnaliser le comportement de la **DataGridView** et **BindingNavigator** en cliquant sur la balise active dans le coin supérieur droit de chacun d’eux :

![DataGridView et la liaison de navigateur des balises actives](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Si les contrôles de votre application a besoin n’est pas disponible dans le **des Sources de données** fenêtre, vous pouvez ajouter des contrôles. Pour plus d’informations, consultez [ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).

Vous pouvez également faire glisser des éléments à partir de la **des Sources de données** fenêtre sur les contrôles déjà sur un formulaire pour lier le contrôle aux données. Un contrôle qui est déjà lié aux données a ses données liaisons redéfinies sur l’élément déplacé sur celui-ci. Pour être des cibles de dépôt valide, contrôles doivent être capables d’afficher le type de données sous-jacent de l’élément glissé sur à partir du **des Sources de données** fenêtre. Par exemple, il n’est pas valide pour faire glisser un élément qui a un type de données de <xref:System.DateTime> sur un <xref:System.Windows.Forms.CheckBox>, car le <xref:System.Windows.Forms.CheckBox> n’est pas capable d’afficher une date.

## <a name="bind-to-data-in-individual-controls"></a>Lier à des données dans des contrôles individuels
Lorsque vous liez une source de données à **détails**, chaque colonne dans le jeu de données est liée à un contrôle séparé.

![Lier la source de données vers les détails](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Notez que dans l’illustration précédente, vous faites glisser à partir de la propriété Orders de la table Customers, et non à partir de la table Orders. En le liant à le `Customer.Orders` propriété, les commandes de navigation effectuées dans le **DataGridView** sont immédiatement répercutées dans les contrôles de détails. Si vous avez fait glisser à partir de la table Orders, les contrôles seraient toujours être liés au jeu de données, mais pas qu’ils ne sont pas synchronisés avec le **DataGridView**.

L’illustration suivante montre la valeur par défaut des contrôles liés aux données qui sont ajoutés au formulaire une fois que la propriété Orders dans la table Customers est liée à **détails** dans le **des Sources de données** fenêtre.

![Table de commandes lié aux détails](../data-tools/media/raddata-orders-table-bound-to-details.png)

Notez également que chaque contrôle a une balise active. Cette balise permet des personnalisations qui s’appliquent à ce contrôle uniquement.

## <a name="see-also"></a>Voir aussi

- [Liaison de contrôles aux données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Liaison de données dans les Windows Forms (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)