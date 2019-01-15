---
title: 'Procédure pas à pas : Création d’un DataTable dans le Concepteur de Dataset'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 505c27787b033a6ccee9f89a19962d5fc81b9912
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824832"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>Procédure pas à pas : Créer un DataTable dans le Concepteur de Dataset

Cette procédure pas à pas explique comment créer un <xref:System.Data.DataTable> (sans TableAdapter) à l’aide de la **Concepteur de Dataset**. Pour plus d’informations sur la création de tables de données comprenant des TableAdapters, consultez [créer et configurer des TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="create-a-new-windows-forms-application"></a>Créer une application Windows Forms

1. Dans Visual Studio, sur le **fichier** menu, sélectionnez **New** > **projet**.

2. Développez le **Visual C#**  ou **Visual Basic** dans le volet gauche, puis sélectionnez **Windows Desktop**.

3. Dans le volet central, sélectionnez le **Windows Forms application** type de projet.

4. Nommez le projet **DataTableWalkthrough**, puis choisissez **OK**.

     Le **DataTableWalkthrough** projet est créé et ajouté à **l’Explorateur de solutions**.

## <a name="add-a-new-dataset-to-the-application"></a>Ajouter un nouveau jeu de données à l’application

1.  Dans le menu **Projet**, sélectionnez **Ajouter un nouvel élément**.

     La boîte de dialogue **Ajouter un nouvel élément** s’affiche.

2.  Dans le volet gauche, sélectionnez **données**, puis sélectionnez **DataSet** dans le volet central.

3.  Sélectionnez **Ajouter**.

     Visual Studio ajoute un fichier appelé **DataSet1.xsd** au projet et l’ouvre dans le **Concepteur de Dataset**.

## <a name="add-a-new-datatable-to-the-dataset"></a>Ajoutez un nouveau DataTable au Dataset

1.  Faites glisser un **DataTable** à partir de la **DataSet** onglet de la **boîte à outils** sur le **Concepteur de Dataset**.

     Une table nommée **DataTable1** est ajouté au jeu de données.

2.  Cliquez sur la barre de titre de **DataTable1** et renommez-le `Music`.

## <a name="add-columns-to-the-datatable"></a>Ajouter des colonnes à la table de données

1.  Cliquez sur le **musique** table. Pointez sur **ajouter**, puis cliquez sur **colonne**.

2.  Nom de la colonne `SongID`.

3.  Dans la fenêtre **Propriétés** , définissez la propriété <xref:System.Data.DataColumn.DataType%2A> sur <xref:System.Int16?displayProperty=fullName>.

4.  Répétez ce processus et ajoutez les colonnes suivantes :

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>Définissez la clé primaire pour la table

Toutes les tables de données doivent avoir une clé primaire. Une clé primaire identifie de façon unique un enregistrement spécifique dans une table de données.

Pour définir la clé primaire, cliquez sur le **SongID** colonne, puis cliquez sur **définir la clé primaire**. Une icône de clé s’affiche en regard du **SongID** colonne.

## <a name="save-your-project"></a>Enregistrer votre projet

Pour enregistrer le **DataTableWalkthrough** projet, dans le **fichier** menu, sélectionnez **Enregistrer tout**.

## <a name="see-also"></a>Voir aussi

- [Créer et configurer des datasets dans Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Validation des données](../data-tools/validate-data-in-datasets.md)