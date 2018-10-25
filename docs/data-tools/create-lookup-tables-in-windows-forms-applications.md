---
title: Créer des tables de recherche dans les applications Windows Forms
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f68cb2178242e5589f312f6ddc2c555da3f47a0e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872822"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Créer des tables de recherche dans les applications Windows Forms
Le terme *table de recherche* décrit les contrôles qui sont liés aux tables de données connexes deux. Ces contrôles de recherche affichent les données à partir de la première table selon une valeur sélectionnée dans la seconde table.

 Vous pouvez créer des tables de recherche en faisant glisser le nœud principal d’une table parent (à partir de la [fenêtre Sources de données](add-new-data-sources.md)) sur un contrôle de votre formulaire qui est déjà lié à la colonne dans la table enfant connexe.

 Par exemple, considérez une table de `Orders` dans une base de données de ventes. Chaque enregistrement dans le `Orders` table inclut un `CustomerID`, indiquant le client ayant passé la commande. Le `CustomerID` est une clé étrangère pointant vers un enregistrement de client dans le `Customers` table. Dans ce scénario, vous développez le `Orders` table dans le **des Sources de données** fenêtre et la valeur est le nœud principal **détails**. Ensuite, définissez le `CustomerID` colonne à utiliser un <xref:System.Windows.Forms.ComboBox> (ou tout autre contrôle qui prend en charge la liaison de correspondance), puis faites glisser le `Orders` nœud vers votre formulaire. Enfin, faites glisser le `Customers` nœud sur le contrôle qui est lié à la colonne associée, dans ce cas, le <xref:System.Windows.Forms.ComboBox> lié à la `CustomerID` colonne.

## <a name="to-databind-a-lookup-control"></a>Pour lier un contrôle de recherche

1.  Ouvrez le **des Sources de données** fenêtre.

    > [!NOTE]
    >  Les tables de recherche nécessitent que les deux tables ou objets connexes sont disponibles dans le **des Sources de données** fenêtre. Pour plus d’informations, consultez [relations dans les datasets](relationships-in-datasets.md).

2.  Développez les nœuds dans le **des Sources de données** fenêtre jusqu'à ce que vous pouvez voir la table parente et toutes ses colonnes et la table enfant connexe et toutes ses colonnes.

    > [!NOTE]
    >  Le nœud de la table enfant est le nœud qui apparaît sous la forme d’un nœud enfant développable dans la table parente.

3.  Modifier le type de déplacement de la table enfant à **détails** en sélectionnant **détails** à partir de la liste de contrôle sur le nœud de la table enfant. Pour plus d’informations, consultez [définir le contrôle à créer lors du déplacement de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4.  Recherchez le nœud qui lie les deux tables (le `CustomerID` nœud dans l’exemple précédent). Modifiez son type de déplacement à un <xref:System.Windows.Forms.ComboBox> en sélectionnant **ComboBox** à partir de la liste de contrôle.

5.  Faites glisser le nœud de la table enfant principale à partir de la **des Sources de données** fenêtre vers votre formulaire.

     Supprimer des contrôles liés aux données (avec des étiquettes descriptives) et un outil (<xref:System.Windows.Forms.BindingNavigator>) apparaissent sur le formulaire. Un [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état du composant.

6.  Maintenant, faites glisser le nœud de la table parent principal à partir de la **des Sources de données** fenêtre directement sur le contrôle de recherche (le <xref:System.Windows.Forms.ComboBox>).

     Les liaisons de recherche sont désormais établis. Consultez le tableau suivant pour les propriétés spécifiques qui ont été définies sur le contrôle.

    |Propriété|Explication du paramètre|
    |--------------| - |
    |**DataSource**|Visual Studio définit cette propriété sur le <xref:System.Windows.Forms.BindingSource>, créé pour la table que vous faites glisser sur le contrôle (par opposition à la <xref:System.Windows.Forms.BindingSource>, créé lorsque le contrôle a été créé).<br /><br /> Si vous avez besoin de faire des réglages, définissez ce paramètre sur le <xref:System.Windows.Forms.BindingSource> de la table contenant la colonne que vous souhaitez afficher.|
    |**DisplayMember**|Visual Studio définit cette propriété sur la première colonne après la clé principale contenant un type de données de chaîne pour la table que vous avez fait glisser vers le contrôle.<br /><br /> Si vous avez besoin de faire des réglages, affectez-lui le nom de colonne que vous souhaitez afficher.|
    |**ValueMember**|Visual Studio définit cette propriété sur la première colonne participant à la clé principale, ou la première colonne de la table si aucune clé n'est définie.<br /><br /> Si vous avez besoin de faire des réglages, affectez la valeur de la clé primaire dans la table avec la colonne que vous souhaitez afficher.|
    |**SelectedValue**|Visual Studio définit cette propriété sur la colonne d’origine est supprimée de la **des Sources de données** fenêtre.<br /><br /> Si vous avez besoin de faire des réglages, affectez la valeur de la colonne de clé étrangère dans la table associée.|

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)