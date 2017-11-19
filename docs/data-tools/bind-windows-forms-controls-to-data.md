---
redirect_url: /visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio
ms.openlocfilehash: 5ba8ada294275a99aab27ff9c249d6c3d8e17da3
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
titre : « des contrôles Windows Forms de liaison aux données | Microsoft Docs » ms.custom : » » ms.date : « 11/04/2016 » ms.reviewer : » « ms.suite : » « ms.tgt_pltfrm : » « ms.topic : « de l’article « helpviewer_keywords : 
  - « affichage des données, des contrôles Windows Forms »
  - « Windows Forms, affichage des données »
  - « sources de données, affichage »
  - « données (Windows Forms), affichage de » ms.assetid : 0163a34a-38cb-40b9-8f38-3058a90caf21 caps.latest.revision : 28 auteur : « gewarren » ms.author : le gestionnaire « gewarren » : ghogen ms.technology : « outils de données Visual Studio »
---
# <a name="bind-windows-forms-controls-to-data"></a>Lier des contrôles Windows Forms à des données
Vous pouvez lier des sources de données aux contrôles en faisant glisser des objets à partir de la **des Sources de données** fenêtre sur un Windows Form ou un contrôle existant sur un formulaire. Avant de faire glisser des éléments, vous pouvez définir le type de contrôle que vous voulez lier. Des valeurs différentes s’affichent selon que vous choisissez la table elle-même, ou une colonne individuelle.  Vous pouvez également définir des valeurs personnalisées. Pour une table, « Détails » signifie que chaque colonne est liée à une commande distincte.  

![Lier la source de données pour le DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata source de données liée au DataGridView")  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="bind-to--data-in-a-datagridview-control"></a>Lier à des données dans un contrôle DataGridView  
Pour le DataGridView, la table entière est liée à ce contrôle unique. Lorsque vous faites glisser un contrôle DataGridView à l’écran, un outil de la frange pour parcourir les enregistrements (<xref:System.Windows.Forms.BindingNavigator>) s’affiche également. A [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état du composant. Dans l’illustration suivante, un TableAdapterManager est également ajouté, car la table Customers a une relation à la table Orders. Ces variables sont déclarées dans le code généré automatiquement en tant que membres privés de la classe de formulaire. Le code généré automatiquement pour remplir le contrôle DataGridView se trouve dans le Gestionnaire d’événements form_load. Le code de l’enregistrement des données pour mettre à jour la base de données se trouve dans le Gestionnaire d’événements de sauvegarde pour le BindingNavigator. Vous pouvez déplacer ou modifier ce code si nécessaire.  
  
 ![GridView avec BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView avec BindingNavigator")  
  
 Vous pouvez personnaliser le comportement du DataGridView et BindingNavigator en cliquant sur la balise active dans le coin supérieur droit de chaque :  
  
 ![DataGridView et liaison le navigateur des balises actives](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView et liaison le navigateur des balises actives")  
  
 Si les contrôles de votre application a besoin n’est pas disponible dans le **des Sources de données** fenêtre, vous pouvez ajouter des contrôles. Pour plus d’informations, consultez [ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 Vous pouvez également faire glisser des éléments à partir de la **des Sources de données** fenêtre vers des contrôles déjà présent sur un formulaire pour lier le contrôle aux données. Un contrôle qui est déjà lié aux données a ses données liaisons redéfinies sur l’élément déplacé sur celui-ci. Pour être des cibles de déplacement valides, les contrôles doivent être capables d’afficher le type de données sous-jacent de l’élément glissé sur à partir du **des Sources de données** fenêtre. Par exemple, il n’est pas valide, faites glisser un élément qui possède un type de données <xref:System.DateTime> sur un <xref:System.Windows.Forms.CheckBox>, car le <xref:System.Windows.Forms.CheckBox> n’est pas capable d’afficher une date.  
  
## <a name="bind-to--data-in-individual-controls"></a>Lier à des données dans des contrôles individuels  
 Lorsque vous liez une source de données à « Détails », chaque colonne dans le jeu de données est liée à une commande distincte.  
  
 ![Lier la source de données vers les détails](../data-tools/media/raddata-bind-data-source-to-details.png "raddata source de données liée aux détails")  
  
> [!IMPORTANT]
>  Notez que dans l’illustration précédente, vous faites glisser à partir de la propriété de commandes de la table Customers, et non à partir de la table Orders. En le liant à la propriété Customer.Orders, les commandes de navigation dans le contrôle DataGridView sont répercutées immédiatement dans les contrôles de détails. Si vous avez fait glisser à partir de la table Orders, les contrôles sont toujours liés au jeu de données, mais pas qu’ils ne sont pas synchronisés avec le contrôle DataGridView.  
  
 L’illustration suivante montre la valeur par défaut des contrôles liés aux données qui sont ajoutés au formulaire une fois la propriété de commandes dans la table Customers est liée à « Détails » dans la **des Sources de données** fenêtre.  
  
 ![Table Orders est lié aux détails](../data-tools/media/raddata-orders-table-bound-to-details.png "raddata commandes tableau lié détails")  
  
 Notez également que chaque contrôle a une balise active. Cette balise permet les personnalisations qui s’appliquent à ce contrôle uniquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)