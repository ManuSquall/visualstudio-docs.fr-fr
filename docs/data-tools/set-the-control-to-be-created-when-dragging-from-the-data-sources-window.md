---
title: Définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre sources de données
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8f5a3cf2d1f34ca9a3d0c2918a8f3f0a3e05260f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281537"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>Définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre Sources de données

Vous pouvez créer des contrôles liés aux données en faisant glisser des éléments depuis la fenêtre **sources de données** vers le Concepteur WPF ou le concepteur de Windows Forms. Chaque élément de la fenêtre **sources de données** a un contrôle par défaut qui est créé lorsque vous le faites glisser vers le concepteur. Toutefois, vous pouvez choisir de créer un contrôle différent.

## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>Définir les contrôles à créer pour les tables de données ou les objets

Avant de faire glisser des éléments qui représentent des tables ou des objets de données à partir de la fenêtre **sources de données** , vous pouvez choisir d’afficher toutes les données dans un contrôle ou d’afficher chaque colonne ou propriété dans un contrôle distinct.

Dans ce contexte, le terme *objet* fait référence à un objet métier personnalisé, à une entité (dans un Entity Data Model) ou à un objet retourné par un service.

### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>Pour définir les contrôles à créer pour les tables de données ou les objets

1. Assurez-vous que le concepteur **WPF** ou le concepteur de **Windows Forms** est ouvert.

2. Dans la fenêtre **sources de données** , sélectionnez l’élément qui représente la table de données ou l’objet que vous souhaitez définir.

   > [!TIP]
   > Si la fenêtre **sources de données** n’est pas ouverte, vous pouvez l’ouvrir en sélectionnant **Afficher**d'  >  **autres**  >  **sources de données**Windows.

3. Cliquez sur le menu déroulant de l’élément, puis cliquez sur l’un des éléments suivants dans le menu :

    - Pour afficher chaque champ de données dans un contrôle séparé, cliquez sur **Détails**. Lorsque vous faites glisser l’élément de données vers le concepteur, cette action crée un contrôle lié aux données différent pour chaque colonne ou propriété de la table de données ou de l’objet parent, ainsi que des étiquettes pour chaque contrôle.

    - Pour afficher toutes les données dans un seul contrôle, sélectionnez un autre contrôle dans la liste, tel que **DataGrid** ou **liste** dans une application WPF, ou **DataGridView** dans une application Windows Forms.

    La liste des contrôles disponibles dépend du concepteur que vous avez ouvert, de la version de .NET que votre projet cible et si vous avez ajouté des contrôles personnalisés qui prennent en charge la liaison de données à la **boîte à outils**. Si le contrôle que vous souhaitez créer ne figure pas dans la liste des contrôles disponibles, vous pouvez ajouter le contrôle à la liste. Pour plus d’informations, consultez [Ajouter des contrôles personnalisés à la fenêtre sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).

    Pour savoir comment créer un contrôle de Windows Forms personnalisé qui peut être ajouté à la liste des contrôles pour les tables de données ou les objets dans la fenêtre **sources de données** , consultez [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données complexe](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).

## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>Définir les contrôles à créer pour les colonnes de données ou les propriétés

Avant de faire glisser un élément qui représente une colonne ou une propriété d’un objet de la fenêtre **sources de données** vers le concepteur, vous pouvez définir le contrôle à créer.

### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>Pour définir les contrôles à créer pour les colonnes ou les propriétés

1. Assurez-vous que le concepteur **WPF** ou le concepteur de **Windows Forms** est ouvert.

2. Dans la fenêtre **sources de données** , développez la table ou l’objet souhaité pour afficher ses colonnes ou ses propriétés.

3. Sélectionnez chaque colonne ou propriété pour laquelle vous souhaitez définir le contrôle à créer.

4. Cliquez sur le menu déroulant de la colonne ou de la propriété, puis sélectionnez le contrôle que vous souhaitez créer lorsque l’élément est déplacé vers le concepteur.

     La liste des contrôles disponibles dépend du concepteur que vous avez ouvert, de la version de .NET que votre projet cible et des contrôles personnalisés qui prennent en charge la liaison de données que vous avez ajoutée à la **boîte à outils**. Si le contrôle que vous souhaitez créer figure dans la liste des contrôles disponibles, vous pouvez ajouter le contrôle à la liste. Pour plus d’informations, consultez [Ajouter des contrôles personnalisés à la fenêtre sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).

     Pour savoir comment créer un contrôle personnalisé qui peut être ajouté à la liste des contrôles pour les colonnes de données ou les propriétés dans la fenêtre **sources de données** , consultez [créer un Windows Forms contrôle utilisateur qui prend en charge la liaison de données simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).

     Si vous ne souhaitez pas créer de contrôle pour la colonne ou la propriété, sélectionnez **aucun** dans le menu déroulant. Cela est utile si vous souhaitez faire glisser la table ou l’objet parent vers le concepteur, mais vous ne souhaitez pas inclure la colonne ou la propriété spécifique.

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
