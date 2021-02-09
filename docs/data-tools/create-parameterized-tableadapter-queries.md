---
title: Créer des requêtes TableAdapter paramétrées
description: Comprendre comment créer des requêtes TableAdapter paramétrées. Une requête paramétrable retourne des données remplissant les conditions d'une clause WHERE dans la requête.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 373e062ad7f2d8600fd28f098cbc0cae1c8d5a65
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859006"
---
# <a name="create-parameterized-tableadapter-queries"></a>Créer des requêtes TableAdapter paramétrées

Une requête paramétrable retourne des données remplissant les conditions d'une clause WHERE dans la requête. Par exemple, vous pouvez paramétrer une liste de clients de sorte à n'afficher que les clients d'une certaine ville en ajoutant `WHERE City = @City` à la fin de l'instruction SQL qui retourne une liste de clients.

Vous créez des requêtes TableAdapter paramétrées dans le **Concepteur de DataSet**. Vous pouvez également les créer dans une application Windows à l’aide de la commande **paramétrer la source de données** dans le menu **données** . La commande **paramétrer la source de données** crée des contrôles sur votre formulaire, où vous pouvez entrer les valeurs des paramètres et exécuter la requête.

> [!NOTE]
> Lors de la construction d’une requête paramétrable, utilisez la notation de paramètre spécifique à la base de données avec laquelle vous codez. Par exemple, les sources de données Access et OleDb utilisent le point d'interrogation « ? » pour désigner des paramètres, la clause WHERE sera donc de type : `WHERE City = ?`.

## <a name="create-a-parameterized-tableadapter-query"></a>Créer une requête TableAdapter paramétrée

### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>Pour créer une requête paramétrée dans le Concepteur de DataSet

- Créez un TableAdapter, en ajoutant une clause WHERE avec les paramètres souhaités à l'instruction SQL. Pour plus d’informations, consultez [créer et configurer des TableAdapters](../data-tools/create-and-configure-tableadapters.md).

     -ou-

- Ajoutez une requête à un TableAdapter existant, en ajoutant une clause WHERE avec les paramètres souhaités à l'instruction SQL.

### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>Pour créer une requête paramétrée pendant la conception d'un formulaire lié aux données

1. Sélectionnez un contrôle dans votre formulaire déjà lié à un dataset. Pour plus d’informations, consultez [lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

2. Dans le menu **données** , sélectionnez **Ajouter une requête**.

3. Utilisez la boîte de dialogue **Générateur de critères de recherche**, en ajoutant une clause WHERE avec les paramètres souhaités à l’instruction SQL.

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>Pour ajouter une requête à un formulaire lié aux données existant

1. Ouvrez le formulaire dans le **Concepteur Windows Forms**.

2. Dans le menu **données** , sélectionnez **Ajouter une requête** ou des **balises actives de données**.

    > [!NOTE]
    > Si l’option **Ajouter une requête** n’est pas disponible dans le menu **Données**, sélectionnez un contrôle dans le formulaire qui affiche la source de données à laquelle ajouter le paramétrage. Par exemple, si le formulaire affiche des données dans un contrôle <xref:System.Windows.Forms.DataGridView>, sélectionnez-le. Si le formulaire affiche des données dans des contrôles individuels, sélectionnez n'importe quel contrôle lié aux données.

3. Dans la zone **Sélectionner une table de source de données** , sélectionnez la table à laquelle vous souhaitez ajouter le paramétrage.

4. Tapez un nom dans la zone **Nom de la nouvelle requête** si vous créez une requête.

     -ou-

     Sélectionnez une requête dans la zone **Nom de la requête existante**.

5. Dans la zone de **texte requête** , tapez une requête qui accepte des paramètres.

6. Sélectionnez **OK**.

     Un contrôle pour entrer le paramètre et un bouton **Charger** sont ajoutés au formulaire dans un contrôle <xref:System.Windows.Forms.ToolStrip>.

### <a name="query-for-null-values"></a>Requête pour les valeurs null

Les paramètres TableAdapter peuvent recevoir des valeurs NULL lorsque vous souhaitez rechercher des enregistrements qui n’ont pas de valeur actuelle. Par exemple, considérez la requête suivante qui a un `ShippedDate` paramètre dans sa `WHERE` clause :

```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

S’il s’agissait d’une requête sur un TableAdapter, vous pouvez interroger toutes les commandes qui n’ont pas été expédiées avec le code suivant :

[!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
[!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]

Pour permettre à une requête d’accepter des valeurs NULL :

1. Dans le **Concepteur de DataSet**, sélectionnez la requête TableAdapter qui doit accepter des valeurs de paramètre null.

2. Dans la fenêtre **Propriétés** , sélectionnez **paramètres**, puis cliquez sur le bouton de sélection (**...**) pour ouvrir l' **éditeur de collections Parameters**.

3. Sélectionnez le paramètre qui autorise les valeurs NULL et affectez à la propriété **AllowDBNull** la valeur `true` .

## <a name="see-also"></a>Voir aussi

- [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
