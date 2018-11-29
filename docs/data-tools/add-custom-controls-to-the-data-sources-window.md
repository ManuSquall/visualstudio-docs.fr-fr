---
title: Ajouter des contrôles personnalisés à la fenêtre Sources de données
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ae05111b1a075515d8011daaf8626e5da7f506e1
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389080"
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>Ajouter des contrôles personnalisés à la fenêtre Sources de données

Lorsque vous faites glisser un élément à partir de la **des Sources de données** fenêtre à une aire de conception pour créer un contrôle lié aux données, vous pouvez sélectionner le type de contrôle que vous créez. Chaque élément dans la fenêtre a une liste déroulante qui affiche les contrôles que vous pouvez choisir. L’ensemble des contrôles associés à chaque élément est déterminé par le type de données de l’élément. Si le contrôle que vous souhaitez créer n’apparaît pas dans la liste, vous pouvez suivre les instructions de cette rubrique pour ajouter le contrôle à la liste.

Pour plus d’informations sur la sélection des contrôles liés aux données pour créer des éléments dans le **des Sources de données** fenêtre, consultez [définir le contrôle à créer lors du déplacement de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="customize-the-bindable-controls-list"></a>Personnaliser la liste de contrôles pouvant être liés

Pour ajouter ou supprimer des contrôles dans la liste des contrôles disponibles pour les éléments dans le **des Sources de données** fenêtre qui ont un type de données spécifique, procédez comme suit.

### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>Pour sélectionner les contrôles à répertorier pour un type de données

1. Assurez-vous que le Concepteur WPF ou le Concepteur de formulaires Windows est ouvert.

2. Dans le **des Sources de données** fenêtre, cliquez sur un élément qui fait partie d’une source de données que vous avez ajouté à la fenêtre, puis cliquez sur le menu déroulant pour l’élément.

   > [!TIP]
   > Si le **des Sources de données** fenêtre n’est pas ouverte, ouvrez-le en sélectionnant **vue** > **Windows autres** > **desSourcesdedonnées**.

3. Dans le menu déroulant, cliquez sur **personnaliser**. Une des boîtes de dialogue suivantes s’ouvre :

    - Si le **Windows Forms Designer** est ouvert, le **personnalisation de l’interface de données** page de la **Options** ouvre la boîte de dialogue.

    - Si le **Concepteur WPF** est ouvert, le **personnaliser la liaison de contrôle** boîte de dialogue s’ouvre.

4. Dans la boîte de dialogue, sélectionnez un type de données à partir de la **type de données** liste déroulante.

    - Pour personnaliser la liste des contrôles pour une table ou d’un objet, sélectionnez **[liste]**.

    - Pour personnaliser la liste des contrôles pour une colonne d’une table ou une propriété d’un objet, sélectionnez le type de données de la colonne ou une propriété dans le magasin de données sous-jacent.

    - Pour personnaliser la liste des contrôles pour afficher les objets de données ayant des formes définies par l’utilisateur, sélectionnez **[autre]**. Par exemple, sélectionnez **[autre]** si votre application comporte un contrôle personnalisé qui affiche les données à partir de plusieurs propriétés d’un objet particulier.

5. Dans le **associés contrôles** zone, sélectionnez chaque contrôle que vous souhaitez être disponible pour le type de données sélectionnée ou désactivez la sélection de tous les contrôles que vous souhaitez supprimer de la liste.

    > [!NOTE]
    > Si le contrôle que vous souhaitez sélectionner n’apparaît pas dans le **associés contrôles** zone, vous devez ajouter le contrôle à la liste. Pour plus d’informations, consultez [ajouter associé contrôles](#add-associated-controls).

6. Cliquez sur **OK**.

7. Dans le **des Sources de données** fenêtre, cliquez sur un élément des données de type que vous venez d’associer un ou plusieurs contrôles, puis cliquez sur le menu déroulant pour l’élément.

     Les contrôles que vous avez sélectionné dans le **associés contrôles** boîte apparaissent désormais dans le menu déroulant pour l’élément.

## <a name="add-associated-controls"></a>Ajouter des contrôles associés

Si vous souhaitez associer un contrôle à un type de données, mais le contrôle n’apparaît pas dans le **associés contrôles** zone, vous devez ajouter le contrôle à la liste. Le contrôle doit être situé dans la solution actuelle ou dans un assembly référencé. Il doit également être disponible dans le **boîte à outils** et avoir un attribut qui spécifie le comportement de liaison de données du contrôle.

### <a name="to-add-controls-to-the-list-of-associated-controls"></a>Pour ajouter des contrôles à la liste des contrôles associés

1. Ajouter le contrôle souhaité pour le **boîte à outils** en double-cliquant sur le **boîte à outils** et en sélectionnant **choisir des éléments de**.

     Le contrôle doit avoir un des attributs suivants.

    |Attribut|Description|
    |---------------|-----------------|
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Implémenter cet attribut sur des contrôles simples qui affichent une seule colonne (ou propriété) de données, comme un <xref:System.Windows.Forms.TextBox>.|
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Implémenter cet attribut sur des contrôles qui affichent des listes (ou tables) de données, comme un <xref:System.Windows.Forms.DataGridView>.|
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Implémenter cet attribut sur des contrôles qui affichent des listes (ou tables) de données, mais doivent également présenter une seule colonne ou une propriété, comme un <xref:System.Windows.Forms.ComboBox>.|

2. Pour les Windows Forms, sur le **Options** boîte de dialogue, ouvrez le **personnalisation de l’interface de données** page. Ou, pour WPF, ouvrez le **personnaliser la liaison de contrôle** boîte de dialogue. Pour plus d’informations, consultez [personnaliser la liste des contrôles pouvant être liés pour un type de données](#customize-the-bindable-controls-list).

3. Dans le **associés contrôles** zone, le contrôle que vous venez d’ajouter à la **boîte à outils** doit maintenant apparaître.

    > [!NOTE]
    > Seuls contrôles qui se trouvent dans la solution actuelle ou dans un assembly référencé peuvent être ajoutés à la liste des contrôles associés. (Les contrôles doivent également implémenter un des attributs de liaison de données dans le tableau précédent.) Pour lier des données à un contrôle personnalisé qui n’est pas disponible dans le **des Sources de données** fenêtre, faites glisser le contrôle de la **boîte à outils** sur l’aire de conception, puis faites glisser l’élément à lier à partir de la **données Sources** fenêtre sur le contrôle.

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)