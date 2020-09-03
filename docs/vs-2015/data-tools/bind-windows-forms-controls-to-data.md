---
title: Lier des contrôles de Windows Forms à des données | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- displaying data, Windows Forms controls
- Windows Forms, displaying data
- data sources, displaying
- data [Windows Forms], displaying
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3cf93d96594b65b06670567e8c23cd83ccb7f1ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672970"
---
# <a name="bind-windows-forms-controls-to-data"></a>Lier des contrôles Windows Forms à des données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez lier des sources de données à des contrôles en faisant glisser des objets depuis la fenêtre **sources de données** vers un Windows Form ou vers un contrôle existant sur un formulaire. Avant de faire glisser des éléments, vous pouvez définir le type de contrôle auquel vous souhaitez effectuer la liaison. Différentes valeurs s’affichent selon que vous choisissez la table elle-même ou une colonne individuelle.  Vous pouvez également définir des valeurs personnalisées. Pour une table, « Details » signifie que chaque colonne est liée à un contrôle distinct.

 ![Lier la source de données à DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata lier la source de données à DataGridView")

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="bind-to--data-in-a-datagridview-control"></a>Lier à des données dans un contrôle DataGridView
 Pour DataGridView, la table entière est liée à ce contrôle unique. Lorsque vous faites glisser un DataGridView vers le formulaire, une barre d’outils pour parcourir les enregistrements ( <xref:System.Windows.Forms.BindingNavigator> ) s’affiche également. Un [DataSet](../data-tools/dataset-tools-in-visual-studio.md), un TableAdapter, <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator> apparaissent dans la barre d’état des composants. Dans l’illustration suivante, un TableAdapterManager est également ajouté, car la table Customers a une relation avec la table Orders. Ces variables sont toutes déclarées dans le code généré automatiquement comme membres privés dans la classe Form. Le code généré automatiquement pour le remplissage du DataGridView se trouve dans le gestionnaire d’événements form_load. Le code permettant d’enregistrer les données pour mettre à jour la base de données se trouve dans le gestionnaire d’événements Save pour le BindingNavigator. Vous pouvez déplacer ou modifier ce code en fonction des besoins.

 ![GridView avec BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView avec BindingNavigator")

 Vous pouvez personnaliser le comportement du DataGridView et du BindingNavigator en cliquant sur la balise active dans le coin supérieur droit de chaque :

 ![Balises actives des navigateurs DataGridView et de liaison](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "balises actives du DataGridView raddata et de l’navigateur de liaisons")

 Si les contrôles nécessaires à votre application ne sont pas disponibles dans la fenêtre **sources de données** , vous pouvez ajouter des contrôles. Pour plus d’informations, consultez [Ajouter des contrôles personnalisés à la fenêtre sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).

 Vous pouvez également faire glisser des éléments depuis la fenêtre **sources de données** vers des contrôles qui se trouvent déjà sur un formulaire pour lier le contrôle aux données. Les liaisons de données d’un contrôle qui est déjà lié à des données sont réinitialisées sur l’élément le plus récemment déplacé vers celui-ci. Pour être des cibles de dépôt valides, les contrôles doivent pouvoir afficher le type de données sous-jacent de l’élément déplacé dans la fenêtre **sources de données** . Par exemple, il n’est pas possible de faire glisser un élément dont le type de données <xref:System.DateTime> <xref:System.Windows.Forms.CheckBox> est vers, car le <xref:System.Windows.Forms.CheckBox> ne peut pas afficher une date.

## <a name="bind-to--data-in-individual-controls"></a>Lier à des données dans des contrôles individuels
 Lorsque vous liez une source de données à « Details », chaque colonne du DataSet est liée à un contrôle distinct.

 ![Lier la source de données aux détails](../data-tools/media/raddata-bind-data-source-to-details.png "raddata lier la source de données aux détails")

> [!IMPORTANT]
> Notez que dans l’illustration précédente, vous faites glisser à partir de la propriété Orders de la table Customers, et non de la table Orders. En liant la propriété Customer. Orders, les commandes de navigation effectuées dans le DataGridView sont reflétées immédiatement dans les contrôles de détails. Si vous faites glisser à partir de la table Orders, les contrôles sont toujours liés au DataSet, mais ils ne sont pas synchronisés avec le DataGridView.

 L’illustration suivante montre les contrôles liés aux données par défaut qui sont ajoutés au formulaire après la liaison de la propriété Orders dans la table Customers à « Details » dans la fenêtre **sources de données** .

 ![Table Orders liée aux détails](../data-tools/media/raddata-orders-table-bound-to-details.png "table raddata Orders liée aux détails")

 Notez également que chaque contrôle a une balise active. Cette balise active les personnalisations qui s’appliquent uniquement à ce contrôle.

## <a name="see-also"></a>Voir aussi
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
