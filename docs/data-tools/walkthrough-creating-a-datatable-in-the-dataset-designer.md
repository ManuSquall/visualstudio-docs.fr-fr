---
title: Créer un DataTable dans le Concepteur de DataSet
description: Dans cette procédure pas à pas, vous créez un DataTable (sans TableAdapter) à l’aide de l’Concepteur de DataSet. Créer une application de Windows Forms et y ajouter un nouveau jeu de données.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: feec31fa0a9e34ad63e0b849d09084081e5710e5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858174"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>Procédure pas à pas : création d’un DataTable dans le Concepteur de DataSet

Cette procédure pas à pas explique comment créer un <xref:System.Data.DataTable> (sans TableAdapter) à l’aide de l' **Concepteur de DataSet**. Pour plus d’informations sur la création de tables de données qui incluent des TableAdapters, consultez [créer et configurer des TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="create-a-new-windows-forms-application"></a>Créer une application Windows Forms

1. Dans Visual Studio, dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**.

2. Développez **Visual C#** ou **Visual Basic** dans le volet gauche, puis sélectionnez **Bureau Windows**.

3. Dans le volet central, sélectionnez le type de projet d' **application Windows Forms** .

4. Nommez le projet **DataTableWalkthrough**, puis choisissez **OK**.

     Le projet **DataTableWalkthrough** est créé et ajouté à **Explorateur de solutions**.

## <a name="add-a-new-dataset-to-the-application"></a>Ajouter un nouveau jeu de données à l’application

1. Dans le menu **Projet**, sélectionnez **Ajouter un nouvel élément**.

     La boîte de dialogue **Ajouter un nouvel élément** s'affiche.

2. Dans le volet gauche, sélectionnez **données**, puis sélectionnez **DataSet** dans le volet central.

3. Choisissez **Ajouter**.

     Visual Studio ajoute un fichier appelé **DataSet1. xsd** au projet et l’ouvre dans le **Concepteur de DataSet**.

## <a name="add-a-new-datatable-to-the-dataset"></a>Ajouter un nouveau DataTable au DataSet

1. Faites glisser un **DataTable** de l’onglet **DataSet** de la **boîte à outils** vers le **Concepteur de DataSet**.

     Une table nommée **DataTable1** est ajoutée au DataSet.

2. Cliquez sur la barre de titre de **DataTable1** et renommez-la `Music` .

## <a name="add-columns-to-the-datatable"></a>Ajouter des colonnes au DataTable

1. Cliquez avec le bouton droit sur la table **Music** . Pointez sur **Ajouter**, puis cliquez sur **colonne**.

2. Nommez la colonne `SongID` .

3. Dans la fenêtre **Propriétés** , définissez la propriété <xref:System.Data.DataColumn.DataType%2A> sur <xref:System.Int16?displayProperty=fullName>.

4. Répétez ce processus et ajoutez les colonnes suivantes :

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>Définir la clé primaire de la table

Toutes les tables de données doivent avoir une clé primaire. Une clé primaire identifie de façon unique un enregistrement spécifique dans une table de données.

Pour définir la clé primaire, cliquez avec le bouton droit sur la colonne **SONGID** , puis cliquez sur **définir la clé primaire**. Une icône de clé apparaît en regard de la colonne **SONGID** .

## <a name="save-your-project"></a>Enregistrer votre projet

Pour enregistrer le projet **DataTableWalkthrough** , dans le menu **fichier** , sélectionnez **enregistrer tout**.

## <a name="see-also"></a>Voir aussi

- [Créer et configurer des datasets dans Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Validation des données](../data-tools/validate-data-in-datasets.md)
