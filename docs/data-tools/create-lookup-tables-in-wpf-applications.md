---
title: Créer des tables de recherche dans des applications WPF
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c76f769234d8b8c14ccd44d8c2cf4c669bf48ffd
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305479"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Créer des tables de recherche dans des applications WPF

Le terme *table de recherche* (parfois appelé un *liaison de correspondance*) décrit un contrôle qui affiche des informations à partir d’une table de données basée sur la valeur d’un champ de clé étrangère dans une autre table. Vous pouvez créer une table de recherche en faisant glisser le nœud principal d’une table parente ou de l’objet dans le **des Sources de données** fenêtre sur un contrôle qui est déjà lié à une colonne ou une propriété dans une table enfant connexe.

Par exemple, considérez une table de `Orders` dans une base de données de ventes. Chaque enregistrement dans le `Orders` table inclut un `CustomerID` qui indique le client ayant passé la commande. Le `CustomerID` est une clé étrangère qui pointe vers un enregistrement de client dans le `Customers` table. Lorsque vous affichez une liste de commandes à partir de la `Orders` table, vous souhaiterez afficher le nom réel au lieu du `CustomerID`. Étant donné que le nom du client est dans le `Customers` table, vous devez créer une table de recherche pour afficher le nom du client. La table de recherche utilise le `CustomerID` valeur dans le `Orders` d’eux pour naviguer jusqu'à la relation et retourne le nom du client.

## <a name="to-create-a-lookup-table"></a>Pour créer une table de choix

1.  Ajoutez l’un des types suivants de sources de données avec les données associées à votre projet :

    -   Jeu de données ou Entity Data Model.

    -   Service de données WCF, service WCF ou service web. Pour plus d’informations, consultez [Comment : se connecter aux données dans un Service](../data-tools/how-to-connect-to-data-in-a-service.md).

    -   Objects Pour plus d’informations, consultez [lier des objets dans Visual Studio](bind-objects-in-visual-studio.md).

    > [!NOTE]
    > Avant de pouvoir créer une table de recherche, les deux tables ou objets connexes doivent exister en tant que source de données pour le projet.

2.  Ouvrez le **Concepteur WPF**et vous assurer que le concepteur contient un conteneur qui est une cible de dépôt valide pour les éléments dans le **Sources de données** fenêtre.

     Pour plus d’informations sur les cibles de dépôt valides, consultez [WPF de lier des contrôles à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

3.  Dans le menu Données **, cliquez sur Afficher les sources de données** pour ouvrir la fenêtre Sources de données **.

4.  Développez les nœuds dans le **des Sources de données** fenêtre, jusqu'à ce que vous pouvez voir la table parente ou objet et la table enfant connexe ou l’objet.

    > [!NOTE]
    > La table enfant connexe ou l’objet est le nœud qui apparaît sous la forme d’un nœud enfant développable sous la table parente ou l’objet.

5.  Cliquez sur le menu déroulant pour le nœud enfant, puis sélectionnez **détails**.

6.  Développez le nœud enfant.

7.  Sous le nœud enfant, cliquez sur le menu déroulant pour l’élément qui lie les données parentes et enfants. (Dans l’exemple précédent, il s’agit du **CustomerID** nœud.) Sélectionnez un des types suivants de contrôles qui prennent en charge la liaison de correspondance :

    -   **ComboBox**

    -   **ListBox**

    -   **ListView**

        > [!NOTE]
        > Si le **ListBox** ou **ListView** contrôle n’apparaît pas dans la liste, vous pouvez ajouter ces contrôles à la liste. Pour plus d’informations, consultez [définir le contrôle à créer lors du déplacement de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    -   N’importe quel contrôle personnalisé qui dérive de <xref:System.Windows.Controls.Primitives.Selector>.

        > [!NOTE]
        > Pour plus d’informations sur l’ajout de contrôles personnalisés à la liste des contrôles vous pouvez sélectionner des éléments dans le **des Sources de données** fenêtre, consultez [ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).

8.  Faites glisser le nœud enfant à partir de la **des Sources de données** fenêtre sur un conteneur dans le Concepteur WPF. (Dans l’exemple précédent, le nœud enfant est la **commandes** nœud.)

     Visual Studio génère le XAML qui crée des contrôles liés aux données pour chacun des éléments que vous faites glisser. Le XAML ajoute également un nouveau <xref:System.Windows.Data.CollectionViewSource> pour l’objet pour les ressources de la cible de déplacement ou la table enfant. Pour certaines sources de données, Visual Studio génère également du code pour charger des données dans la table ou l’objet. Pour plus d’informations, consultez [WPF de lier des contrôles à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

9. Faites glisser le nœud parent à partir de la **des Sources de données** fenêtre sur le contrôle de liaison de recherche que vous avez créé précédemment. (Dans l’exemple précédent, le nœud parent est la **clients** nœud).

     Visual Studio définit certaines propriétés sur le contrôle pour configurer la liaison de la recherche. Le tableau suivant répertorie les propriétés Visual Studio modifie. Si nécessaire, vous pouvez modifier ces propriétés dans le XAML ou dans le **propriétés** fenêtre.

    |Property|Explication du paramètre|
    |--------------| - |
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Cette propriété spécifie la collection ou liaison qui est utilisée pour obtenir les données qui s’affiche dans le contrôle. Visual Studio définit cette propriété sur le <xref:System.Windows.Data.CollectionViewSource> pour les données parent que vous avez fait glisser vers le contrôle.|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Cette propriété spécifie le chemin d’accès de l’élément de données qui s’affiche dans le contrôle. Visual Studio définit cette propriété pour la première colonne ou propriété dans les données parent, après la clé primaire, ce qui a un type de données de chaîne.<br /><br /> Si vous souhaitez afficher une autre colonne ou une propriété dans les données parentes, modifiez cette propriété pour le chemin d’accès d’une autre propriété.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio lie cette propriété à la colonne ou la propriété des données enfant que vous avez fait glisser vers le concepteur. Il s’agit de la clé étrangère aux données parent.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio définit cette propriété sur le chemin d’accès de la colonne ou propriété des données enfant qui sont la clé étrangère aux données parent.|

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Afficher des données associées dans des applications WPF](../data-tools/display-related-data-in-wpf-applications.md)
- [Procédure pas à pas : affichage de données connexes dans une application WPF](../data-tools/display-related-data-in-wpf-applications.md)