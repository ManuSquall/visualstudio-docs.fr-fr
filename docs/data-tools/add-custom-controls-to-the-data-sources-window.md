---
title: Ajouter des contrôles personnalisés à la fenêtre Sources de données
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.datasource.howtoaddcustomcontrol
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
author: ghogen
ms.author: ghogen
manager: jillfra
ms.openlocfilehash: 39ff272581793be9b456bbc404119a488850b3c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283071"
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>Ajouter des contrôles personnalisés à la fenêtre Sources de données

Quand vous faites glisser un élément de la fenêtre sources de données vers une aire de conception pour créer un contrôle lié aux données, vous pouvez sélectionner le type de contrôle que vous créez. Chaque élément de la fenêtre contient une liste déroulante qui affiche les contrôles parmi lesquels vous pouvez choisir. L’ensemble de contrôles associés à chaque élément est déterminé par le type de données de l’élément. Si le contrôle que vous souhaitez créer ne figure pas dans la liste, vous pouvez suivre les instructions de cette rubrique pour ajouter le contrôle à la liste.

Pour plus d’informations sur la sélection des contrôles liés aux données à créer pour les éléments dans la fenêtre sources de données, consultez [définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="customize-the-bindable-controls-list"></a>Personnaliser la liste des contrôles pouvant être liés

Pour ajouter ou supprimer des contrôles dans la liste des contrôles disponibles pour les éléments de la fenêtre sources de données qui ont un type de données spécifique, procédez comme suit.

### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>Pour sélectionner les contrôles à répertorier pour un type de données

1. Assurez-vous que le Concepteur WPF ou le Concepteur Windows Forms est ouvert.

2. Dans la fenêtre **sources de données** , cliquez sur un élément qui fait partie d’une source de données que vous avez ajoutée à la fenêtre, puis cliquez sur le menu déroulant de l’élément.

   > [!TIP]
   > Si la fenêtre sources de données n’est pas ouverte, ouvrez-la en sélectionnant **Afficher**d'  >  **autres**  >  **sources de données**Windows.

3. Dans le menu déroulant, cliquez sur **personnaliser**. L’une des boîtes de dialogue suivantes s’ouvre :

    - Si le **Concepteur Windows Forms** est ouvert, la page Personnalisation de l' **interface utilisateur de données** de la boîte de dialogue **options** s’ouvre. Pour plus d’informations, consultez [boîte de dialogue Options de personnalisation de l’interface utilisateur de données](../ide/reference/options-windows-forms-designer-data-ui-customization.md).

    - Si le **Concepteur WPF** est ouvert, la boîte de dialogue **personnaliser la liaison de contrôle** s’ouvre.

4. Dans la boîte de dialogue, sélectionnez un type de données dans la liste déroulante **type de données** .

    - Pour personnaliser la liste des contrôles pour une table ou un objet, sélectionnez **[liste]**.

    - Pour personnaliser la liste des contrôles d’une colonne d’une table ou d’une propriété d’un objet, sélectionnez le type de données de la colonne ou de la propriété dans le magasin de données sous-jacent.

    - Pour personnaliser la liste des contrôles afin d’afficher les objets de données qui ont des formes définies par l’utilisateur, sélectionnez **[autre]**. Par exemple, sélectionnez **[autre]** si votre application possède un contrôle personnalisé qui affiche des données provenant de plusieurs propriétés d’un objet particulier.

5. Dans la zone **contrôles associés** , sélectionnez chaque contrôle que vous souhaitez utiliser pour le type de données sélectionné, ou désactivez la sélection des contrôles que vous souhaitez supprimer de la liste.

    > [!NOTE]
    > Si le contrôle que vous souhaitez sélectionner n’apparaît pas dans la zone **contrôles associés** , vous devez ajouter le contrôle à la liste. Pour plus d’informations, consultez [Ajouter des contrôles associés](#add-associated-controls).

6. Cliquez sur **OK**.

7. Dans la fenêtre **sources de données** , cliquez sur un élément du type de données que vous venez de associer à un ou plusieurs contrôles, puis cliquez sur le menu déroulant de l’élément.

     Les contrôles que vous avez sélectionnés dans la zone **contrôles associés** s’affichent désormais dans le menu déroulant de l’élément.

## <a name="add-associated-controls"></a>Ajouter des contrôles associés

Si vous souhaitez associer un contrôle à un type de données, mais que le contrôle n’apparaît pas dans la zone **contrôles associés** , vous devez ajouter le contrôle à la liste. Le contrôle doit se trouver dans la solution actuelle ou dans un assembly référencé. Elle doit également être disponible dans la **boîte à outils** et avoir un attribut qui spécifie le comportement de liaison de données du contrôle.

Pour ajouter des contrôles à la liste des contrôles associés :

1. Ajoutez le contrôle souhaité à la **boîte à outils** en cliquant avec le bouton droit sur la **boîte à outils** et en sélectionnant **choisir les éléments**.

     Le contrôle doit avoir l’un des attributs suivants :

    |Attribut|Description|
    |---------------|-----------------|
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Implémentez cet attribut sur des contrôles simples qui affichent une seule colonne (ou propriété) de données, par exemple <xref:System.Windows.Forms.TextBox> .|
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Implémentez cet attribut sur des contrôles qui affichent des listes (ou tables) de données, telles qu’un <xref:System.Windows.Forms.DataGridView> .|
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Implémentez cet attribut sur des contrôles qui affichent des listes (ou tables) de données, mais qui doivent également présenter une seule colonne ou propriété, telle qu’un <xref:System.Windows.Forms.ComboBox> .|

2. Par Windows Forms, dans la boîte de dialogue **options** , ouvrez la page Personnalisation de l' **interface utilisateur des données** . Ou, pour WPF, ouvrez la boîte de dialogue **personnaliser la liaison de contrôle** . Pour plus d’informations, consultez [personnaliser la liste des contrôles pouvant être liés pour un type de données](#customize-the-bindable-controls-list).

3. Dans la zone **contrôles associés** , le contrôle que vous venez d’ajouter à la **boîte à outils** doit maintenant apparaître.

    > [!NOTE]
    > Seuls les contrôles qui se trouvent dans la solution actuelle ou dans un assembly référencé peuvent être ajoutés à la liste des contrôles associés. (Les contrôles doivent également implémenter l’un des attributs de liaison de données dans le tableau précédent.) Pour lier des données à un contrôle personnalisé qui n’est pas disponible dans la fenêtre sources de données, faites glisser le contrôle de la **boîte à outils** vers l’aire de conception, puis faites glisser l’élément vers lequel effectuer la liaison à partir de la fenêtre **sources de données** sur le contrôle.

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Boîte de dialogue Options de personnalisation de l’interface utilisateur des données](../ide/reference/options-windows-forms-designer-data-ui-customization.md)
