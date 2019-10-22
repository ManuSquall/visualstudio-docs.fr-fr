---
title: Lier des contrôles Windows Forms à des données
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 24c3549cf98e49f3419ef0e7387a6c236c15e9e6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648843"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Lier des contrôles Windows Forms à des données dans Visual Studio

Vous pouvez afficher des données pour les utilisateurs de votre application en liant des données à Windows Forms. Pour créer ces contrôles liés aux données, faites glisser les éléments de la fenêtre **sources de données** vers le Concepteur Windows Forms dans Visual Studio.

![Opération glisser de source de données](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> Si la fenêtre **sources de données** n’est pas visible, vous pouvez l’ouvrir en choisissant **Afficher**  >  d’autres**sources de données** **Windows**  > , ou en appuyant sur **MAJ** +**ALT** +**D**. Pour afficher la fenêtre **sources de données** , vous devez disposer d’un projet ouvert dans Visual Studio.

Avant de faire glisser des éléments, vous pouvez définir le type de contrôle auquel vous souhaitez effectuer la liaison. Différentes valeurs s’affichent selon que vous choisissez la table elle-même ou une colonne individuelle.  Vous pouvez également définir des valeurs personnalisées. Pour une table, les **Détails** signifient que chaque colonne est liée à un contrôle distinct.

![Lier la source de données à DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>Contrôles BindingSource et BindingNavigator

Le composant <xref:System.Windows.Forms.BindingSource> remplit deux fonctions. Tout d’abord, il fournit une couche d’abstraction lors de la liaison des contrôles aux données. Les contrôles du formulaire sont liés au composant <xref:System.Windows.Forms.BindingSource> plutôt qu’à une source de données. Deuxièmement, il peut gérer une collection d’objets. L’ajout d’un type à l' <xref:System.Windows.Forms.BindingSource> crée une liste de ce type.

Pour plus d’informations sur le composant <xref:System.Windows.Forms.BindingSource>, consultez :

- [BindingSource, composant](/dotnet/framework/winforms/controls/bindingsource-component)

- [Vue d’ensemble du composant BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [Architecture du composant BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

Le [contrôle BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) fournit une interface utilisateur qui permet de naviguer dans les données affichées par une application Windows.

## <a name="bind-to-data-in-a-datagridview-control"></a>Lier à des données dans un contrôle DataGridView

Pour un [contrôle DataGridView](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), la totalité de la table est liée à ce contrôle unique. Lorsque vous faites glisser un **DataGridView** vers le formulaire, une barre d’outils pour parcourir les enregistrements (<xref:System.Windows.Forms.BindingNavigator>) s’affiche également. Un [jeu de données](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator> apparaissent dans la barre d’état des composants. Dans l’illustration suivante, un [TableAdapterManager](https://msdn.microsoft.com/library/bb384426.aspx) est également ajouté, car la table Customers a une relation avec la table Orders. Ces variables sont toutes déclarées dans le code généré automatiquement comme membres privés dans la classe Form. Le code généré automatiquement pour le remplissage du **DataGridView** se trouve dans le gestionnaire d’événements `Form_Load`. Le code permettant d’enregistrer les données pour mettre à jour la base de données se trouve dans le gestionnaire d’événements `Save` pour le **BindingNavigator**. Vous pouvez déplacer ou modifier ce code en fonction des besoins.

![GridView avec BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

Vous pouvez personnaliser le comportement du **DataGridView** et du **BindingNavigator** en cliquant sur la balise active dans le coin supérieur droit de chaque :

![Balises actives des navigateurs DataGridView et de liaison](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Si les contrôles nécessaires à votre application ne sont pas disponibles dans la fenêtre **sources de données** , vous pouvez ajouter des contrôles. Pour plus d’informations, consultez [Ajouter des contrôles personnalisés à la fenêtre sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).

Vous pouvez également faire glisser des éléments depuis la fenêtre **sources de données** vers des contrôles qui se trouvent déjà sur un formulaire pour lier le contrôle aux données. Les liaisons de données d’un contrôle qui est déjà lié à des données sont réinitialisées sur l’élément le plus récemment déplacé vers celui-ci. Pour être des cibles de dépôt valides, les contrôles doivent pouvoir afficher le type de données sous-jacent de l’élément déplacé dans la fenêtre **sources de données** . Par exemple, il n’est pas possible de faire glisser un élément dont le type de données est <xref:System.DateTime> sur un <xref:System.Windows.Forms.CheckBox>, car le <xref:System.Windows.Forms.CheckBox> ne peut pas afficher une date.

## <a name="bind-to-data-in-individual-controls"></a>Lier à des données dans des contrôles individuels

Lorsque vous liez une source de données à des **Détails**, chaque colonne du DataSet est liée à un contrôle distinct.

![Lier la source de données aux détails](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Notez que dans l’illustration précédente, vous faites glisser à partir de la propriété Orders de la table Customers, et non de la table Orders. En liant la propriété `Customer.Orders`, les commandes de navigation effectuées dans le **DataGridView** sont reflétées immédiatement dans les contrôles de détails. Si vous faites glisser à partir de la table Orders, les contrôles sont toujours liés au DataSet, mais ils ne sont pas synchronisés avec le **DataGridView**.

L’illustration suivante montre les contrôles liés aux données par défaut qui sont ajoutés au formulaire après la liaison de la propriété Orders dans la table Customers aux **Détails** dans la fenêtre **sources de données** .

![Table Orders liée aux détails](../data-tools/media/raddata-orders-table-bound-to-details.png)

Notez également que chaque contrôle a une balise active. Cette balise active les personnalisations qui s’appliquent uniquement à ce contrôle.

## <a name="see-also"></a>Voir aussi

- [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Liaison de données en Windows Forms (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)