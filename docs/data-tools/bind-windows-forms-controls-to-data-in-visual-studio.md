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
ms.openlocfilehash: e89a919f6f93dc70f9417a23430c960f03cf92bb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Lier des contrôles Windows Forms à des données dans Visual Studio
Vous pouvez afficher des données pour les utilisateurs de votre application en liant des données à des Windows Forms. Pour créer ces contrôles liés aux données, vous pouvez faire glisser des éléments à partir de la **des Sources de données** fenêtre sur le Concepteur Windows Forms dans Visual Studio.

![Opération de glissement de Source de données](../data-tools/media/raddata-data-source-drag-operation.png "opération de glissement de raddata Source de données")

Avant de faire glisser des éléments, vous pouvez définir le type de contrôle que vous voulez lier. Des valeurs différentes s’affichent selon que vous choisissez la table elle-même, ou une colonne individuelle.  Vous pouvez également définir des valeurs personnalisées. Pour une table, « Détails » signifie que chaque colonne est liée à une commande distincte.

![Lier la source de données pour le DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata source de données liée au DataGridView")

## <a name="bindingsource-and-bindingnavigator-controls"></a>BindingSource et contrôles de BindingNavigator
Le composant <xref:System.Windows.Forms.BindingSource> remplit deux fonctions. Tout d’abord, il fournit une couche d’abstraction lors de la liaison des contrôles aux données. Contrôles du formulaire sont liés à la <xref:System.Windows.Forms.BindingSource> composant au lieu de directement à une source de données. En second lieu, il peut gérer une collection d’objets. Ajout d’un type à la <xref:System.Windows.Forms.BindingSource> crée une liste de ce type.

Pour plus d’informations sur le <xref:System.Windows.Forms.BindingSource> composant, consultez :

-   [BindingSource, composant](/dotnet/framework/winforms/controls/bindingsource-component)

-   [Vue d'ensemble du composant BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)

-   [Architecture du composant BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

Le [contrôle BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) fournit une interface utilisateur pour naviguer dans les données affichées par une application Windows.

## <a name="bind-to-data-in-a-datagridview-control"></a>Lier à des données dans un contrôle DataGridView
Pour un [contrôle DataGridView](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), la table entière est liée à ce contrôle unique. Lorsque vous faites glisser un contrôle DataGridView à l’écran, un outil de la frange pour parcourir les enregistrements (<xref:System.Windows.Forms.BindingNavigator>) s’affiche également. A [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état du composant. Dans l’illustration suivante, un TableAdapterManager est également ajouté, car la table Customers a une relation à la table Orders. Ces variables sont déclarées dans le code généré automatiquement en tant que membres privés de la classe de formulaire. Le code généré automatiquement pour remplir le contrôle DataGridView se trouve dans le Gestionnaire d’événements form_load. Le code de l’enregistrement des données pour mettre à jour la base de données se trouve dans le Gestionnaire d’événements de sauvegarde pour le BindingNavigator. Vous pouvez déplacer ou modifier ce code si nécessaire.

![GridView avec BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView avec BindingNavigator")

Vous pouvez personnaliser le comportement du DataGridView et BindingNavigator en cliquant sur la balise active dans le coin supérieur droit de chaque :

![DataGridView et liaison le navigateur des balises actives](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView et liaison le navigateur des balises actives")

Si les contrôles de votre application a besoin n’est pas disponible dans le **des Sources de données** fenêtre, vous pouvez ajouter des contrôles. Pour plus d’informations, consultez [ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).

Vous pouvez également faire glisser des éléments à partir de la **des Sources de données** fenêtre vers des contrôles déjà présent sur un formulaire pour lier le contrôle aux données. Un contrôle qui est déjà lié aux données a ses données liaisons redéfinies sur l’élément déplacé sur celui-ci. Pour être des cibles de déplacement valides, les contrôles doivent être capables d’afficher le type de données sous-jacent de l’élément glissé sur à partir du **des Sources de données** fenêtre. Par exemple, il n’est pas valide, faites glisser un élément qui possède un type de données <xref:System.DateTime> sur un <xref:System.Windows.Forms.CheckBox>, car le <xref:System.Windows.Forms.CheckBox> n’est pas capable d’afficher une date.

## <a name="bind-to-data-in-individual-controls"></a>Lier à des données dans des contrôles individuels
Lorsque vous liez une source de données à « Détails », chaque colonne dans le jeu de données est liée à une commande distincte.

![Lier la source de données vers les détails](../data-tools/media/raddata-bind-data-source-to-details.png "raddata source de données liée aux détails")

> [!IMPORTANT]
> Notez que dans l’illustration précédente, vous faites glisser à partir de la propriété de commandes de la table Customers, et non à partir de la table Orders. En le liant à la propriété Customer.Orders, les commandes de navigation dans le contrôle DataGridView sont répercutées immédiatement dans les contrôles de détails. Si vous avez fait glisser à partir de la table Orders, les contrôles sont toujours liés au jeu de données, mais pas qu’ils ne sont pas synchronisés avec le contrôle DataGridView.

L’illustration suivante montre la valeur par défaut des contrôles liés aux données qui sont ajoutés au formulaire une fois la propriété de commandes dans la table Customers est liée à « Détails » dans la **des Sources de données** fenêtre.

![Table Orders est lié aux détails](../data-tools/media/raddata-orders-table-bound-to-details.png "raddata commandes tableau lié détails")

Notez également que chaque contrôle a une balise active. Cette balise permet les personnalisations qui s’appliquent à ce contrôle uniquement.

## <a name="see-also"></a>Voir aussi

- [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Liaison de données dans les Windows Forms (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)