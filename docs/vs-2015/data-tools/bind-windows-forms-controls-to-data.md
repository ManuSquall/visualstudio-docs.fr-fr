---
title: Lier des contrôles Windows Forms à des données | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3541dada6167bd2f0a95913d9ccc385dc3e5ccc3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439472"
---
# <a name="bind-windows-forms-controls-to-data"></a>Lier des contrôles Windows Forms à des données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez lier des sources de données aux contrôles en faisant glisser des objets à partir de la **des Sources de données** fenêtre sur un formulaire Windows ou sur un contrôle existant sur un formulaire. Avant de faire glisser des éléments, vous pouvez définir le type de contrôle que vous souhaitez établir une liaison. Des valeurs différentes s’affichent selon que vous choisissez la table elle-même, ou une colonne individuelle.  Vous pouvez également définir des valeurs personnalisées. Pour une table, « Détails » signifie que chaque colonne est liée à un contrôle séparé.  
  
 ![Lier la source de données à un DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata source de données liée à un DataGridView")  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="bind-to--data-in-a-datagridview-control"></a>Lier à des données dans un contrôle DataGridView  
 Pour DataGridView, la table entière est liée à ce contrôle unique. Lorsque vous faites glisser un DataGridView au formulaire, un outil de la frange pour parcourir les enregistrements (<xref:System.Windows.Forms.BindingNavigator>) s’affiche également. Un [DataSet](../data-tools/dataset-tools-in-visual-studio.md), TableAdapter, <xref:System.Windows.Forms.BindingSource>, et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état du composant. Dans l’illustration suivante, un TableAdapterManager est également ajouté, car la table Customers a une relation avec la table Orders. Ces variables sont déclarées dans le code généré automatiquement en tant que membres privés dans la classe de formulaire. Le code généré automatiquement pour remplir le contrôle DataGridView se trouve dans le Gestionnaire d’événements form_load. Le code pour enregistrer les données pour mettre à jour de la base de données se trouve dans le Gestionnaire d’événements Save pour BindingNavigator. Vous pouvez déplacer ou modifier ce code en fonction des besoins.  
  
 ![GridView avec BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView avec BindingNavigator")  
  
 Vous pouvez personnaliser le comportement du DataGridView et BindingNavigator en cliquant sur la balise active dans le coin supérieur droit de chacun d’eux :  
  
 ![DataGridView et la liaison de navigateur des balises actives](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView et la liaison de navigateur des balises actives")  
  
 Si les contrôles de votre application a besoin n’est pas disponible dans le **des Sources de données** fenêtre, vous pouvez ajouter des contrôles. Pour plus d’informations, consultez [ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 Vous pouvez également faire glisser des éléments à partir de la **des Sources de données** fenêtre sur les contrôles déjà sur un formulaire pour lier le contrôle aux données. Un contrôle qui est déjà lié aux données a ses données liaisons redéfinies sur l’élément déplacé sur celui-ci. Pour être des cibles de dépôt valide, contrôles doivent être capables d’afficher le type de données sous-jacent de l’élément glissé sur à partir du **des Sources de données** fenêtre. Par exemple, il n’est pas valide pour faire glisser un élément qui a un type de données de <xref:System.DateTime> sur un <xref:System.Windows.Forms.CheckBox>, car le <xref:System.Windows.Forms.CheckBox> n’est pas capable d’afficher une date.  
  
## <a name="bind-to--data-in-individual-controls"></a>Lier à des données dans des contrôles individuels  
 Lorsque vous liez une source de données à « Détails », chaque colonne dans le jeu de données est liée à un contrôle séparé.  
  
 ![Lier la source de données vers les détails](../data-tools/media/raddata-bind-data-source-to-details.png "raddata source de données liée aux détails")  
  
> [!IMPORTANT]
> Notez que dans l’illustration précédente, vous faites glisser à partir de la propriété Orders de la table Customers, et non à partir de la table Orders. En le liant à la propriété Customer.Orders, les commandes de navigation dans le contrôle DataGridView sont reflétées immédiatement dans les contrôles de détails. Si vous avez fait glisser à partir de la table Orders, les contrôles seraient toujours liés au jeu de données, mais pas qu’ils ne sont pas synchronisés avec le contrôle DataGridView.  
  
 L’illustration suivante montre la valeur par défaut des contrôles liés aux données qui sont ajoutés au formulaire une fois que la propriété de commandes dans la table Customers est liée à « Détails » dans la **des Sources de données** fenêtre.  
  
 ![Table Orders lié aux détails](../data-tools/media/raddata-orders-table-bound-to-details.png "table de commandes raddata lié aux détails")  
  
 Notez également que chaque contrôle a une balise active. Cette balise permet des personnalisations qui s’appliquent à ce contrôle uniquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
