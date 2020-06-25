---
title: Créer des tables de recherche dans des applications Windows Forms
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9a1ae368b7d2bf8548bf78a6a9795e19206bc277
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282655"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Créer des tables de recherche dans des applications Windows Forms

La *table de recherche* de terme décrit les contrôles liés à deux tables de données associées. Ces contrôles de recherche affichent les données de la première table en fonction d’une valeur sélectionnée dans la seconde table.

Vous pouvez créer des tables de recherche en faisant glisser le nœud principal d’une table parente (à partir de la [fenêtre sources de données](add-new-data-sources.md#data-sources-window)) sur un contrôle de votre formulaire qui est déjà lié à la colonne dans la table enfant associée.

Prenons l’exemple d’une table de `Orders` dans une base de données Sales. Chaque enregistrement de la `Orders` table contient un `CustomerID` , indiquant le client qui a passé la commande. `CustomerID`Est une clé étrangère qui pointe vers un enregistrement de client dans la `Customers` table. Dans ce scénario, vous développez la `Orders` table dans la fenêtre **sources de données** et définissez le nœud principal sur **Détails**. Ensuite, définissez la `CustomerID` colonne pour qu’elle utilise un <xref:System.Windows.Forms.ComboBox> (ou tout autre contrôle qui prend en charge la liaison de recherche), puis faites glisser le `Orders` nœud sur votre formulaire. Enfin, faites glisser le `Customers` nœud sur le contrôle lié à la colonne associée, dans ce cas, le <xref:System.Windows.Forms.ComboBox> lié à la `CustomerID` colonne.

## <a name="to-databind-a-lookup-control"></a>Pour lier un contrôle de recherche

1. Une fois votre projet ouvert, ouvrez la fenêtre **sources de données** en sélectionnant **Afficher**d'  >  **autres**  >  **sources de données**Windows.

    > [!NOTE]
    > Les tables de recherche requièrent que deux tables ou objets associés soient disponibles dans la fenêtre **sources de données** . Pour plus d’informations, consultez [relations dans les jeux de données](relationships-in-datasets.md).

2. Développez les nœuds dans la fenêtre **sources de données** jusqu’à ce que vous puissiez voir la table parente et toutes ses colonnes, ainsi que la table enfant associée et toutes ses colonnes.

    > [!NOTE]
    > Le nœud de la table enfant est le nœud qui apparaît en tant que nœud enfant pouvant être développé dans la table parente.

3. Remplacez le type de déplacement de la table enfant par **Détails** en sélectionnant **Détails** dans la liste de contrôles sur le nœud de la table enfant. Pour plus d’informations, consultez [définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4. Localisez le nœud qui lie les deux tables (le `CustomerID` nœud dans l’exemple précédent). Remplacez son type de dépôt <xref:System.Windows.Forms.ComboBox> par un en sélectionnant **ComboBox** dans la liste de contrôles.

5. Faites glisser le nœud principal de la table enfant de la fenêtre **sources de données** vers votre formulaire.

     Les contrôles DataBound (avec des étiquettes descriptives) et une barre d’outils ( <xref:System.Windows.Forms.BindingNavigator> ) s’affichent sur le formulaire. Un [DataSet](../data-tools/dataset-tools-in-visual-studio.md), un [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource> et <xref:System.Windows.Forms.BindingNavigator> apparaissent dans la barre d’état des composants.

6. À présent, faites glisser le nœud de la table parente principale de la fenêtre **sources de données** directement dans le contrôle de recherche (le <xref:System.Windows.Forms.ComboBox> ).

     Les liaisons de recherche sont désormais établies. Reportez-vous au tableau suivant pour les propriétés spécifiques qui ont été définies sur le contrôle.

    |Propriété|Explication du paramètre|
    |--------------| - |
    |**DataSource**|Visual Studio définit cette propriété sur le <xref:System.Windows.Forms.BindingSource> créé pour la table que vous avez fait glisser vers le contrôle (et non sur le <xref:System.Windows.Forms.BindingSource> créé en même temps que le contrôle).<br /><br /> Si vous devez effectuer un ajustement, définissez-le sur le <xref:System.Windows.Forms.BindingSource> de la table avec la colonne que vous souhaitez afficher.|
    |**DisplayMember**|Visual Studio définit cette propriété sur la première colonne après la clé principale contenant un type de données de chaîne pour la table que vous avez fait glisser vers le contrôle.<br /><br /> Si vous devez effectuer un ajustement, définissez cette valeur sur le nom de la colonne que vous souhaitez afficher.|
    |**ValueMember**|Visual Studio définit cette propriété sur la première colonne participant à la clé principale, ou la première colonne de la table si aucune clé n'est définie.<br /><br /> Si vous devez effectuer un ajustement, définissez cette valeur sur la clé primaire de la table avec la colonne que vous souhaitez afficher.|
    |**SelectedValue**|Visual Studio définit cette propriété sur la colonne d’origine déplacée à partir de la fenêtre **sources de données** .<br /><br /> Si vous devez effectuer un ajustement, définissez-la sur la colonne de clé étrangère de la table associée.|

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
