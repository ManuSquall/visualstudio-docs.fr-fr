---
title: Se connecter à des données dans une base de données Access
description: Découvrez comment se connecter aux données d’une base de données Access (un fichier. mdb ou. accdb. file) dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/18/2019
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], connecting
- connecting to data, Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 156acfd56789ec13201738e72c6df283e257e94f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436860"
---
# <a name="connect-to-data-in-an-access-database"></a>Se connecter à des données dans une base de données Access

Vous pouvez vous connecter à une base de données Access (fichier *. mdb* ou *. accdb* ) à l’aide de Visual Studio. Après avoir défini la connexion, les données s’affichent dans la fenêtre **Sources de données**. À partir de là, vous pouvez faire glisser des tables ou des vues sur votre aire de conception.

## <a name="prerequisites"></a>Prérequis

Pour utiliser ces procédures, vous avez besoin d’un projet Windows Forms ou WPF et d’une base de données Access (fichier *. accdb* ) ou d’une base de données Access 2000-2003 (fichier *. mdb* ). Suivez la procédure qui correspond à votre type de fichier.

## <a name="create-a-dataset-for-an-accdb-file"></a>Créer un jeu de données pour un fichier. accdb

Connectez-vous aux bases de données créées avec Microsoft 365, Access 2013, Access 2010 ou Access 2007 à l’aide de la procédure suivante.

1. Ouvrez un Windows Forms ou un projet d’application WPF dans Visual Studio.

2. Pour ouvrir la fenêtre **sources de données** , dans le menu **affichage** , sélectionnez autres sources de **Other Windows**  >  **données** Windows.

   ![Afficher d'autres sources de données Windows](../data-tools/media/viewdatasources.png)

3. Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.

   L' **Assistant Configuration de source de données** s’ouvre.

4. Sélectionnez **base de données** dans la page **choisir un type de source de données** , puis sélectionnez **suivant**.

5. Sélectionnez **DataSet** dans la page **choisir un modèle de base de données** , puis sélectionnez **suivant**.

6. Dans la page **Choisir votre connexion de données** , sélectionnez **Nouvelle connexion** pour configurer une nouvelle connexion de données.

   La boîte de dialogue **Ajouter une connexion** s’ouvre.

7. Si la **source de données** n’est pas définie sur **fichier de base de données Microsoft Access** , sélectionnez le bouton **modifier** .

   La boîte de dialogue **modifier la source de données** s’ouvre. Dans la liste des sources de données, choisissez **fichier de base de données Microsoft Access**. Dans la liste déroulante **fournisseur de données** , sélectionnez **.NET Framework fournisseur de données pour OLE DB** , puis choisissez **OK**.

8. Choisissez **Parcourir** en regard de **nom du fichier de base de données** , puis accédez à votre fichier *. accdb* et choisissez **ouvrir**.

9. Entrez un nom d’utilisateur et un mot de passe (si nécessaire), puis choisissez **OK**.

10. Sélectionnez **suivant** dans la page **choisir votre connexion de données** .

    Vous pouvez obtenir une boîte de dialogue indiquant que le fichier de données ne se trouve pas dans votre projet actuel. Sélectionnez **Oui** ou **non**.

11. Sélectionnez **suivant** dans la page **enregistrer la chaîne de connexion dans le fichier de configuration de l’application** .

12. Développez le nœud **tables** dans la page **choisir vos objets de base de données** .

13. Sélectionnez les tables ou les vues que vous souhaitez inclure dans votre jeu de données, puis sélectionnez **Terminer**.

    Le jeu de données est ajouté à votre projet, et les tables et vues s’affichent dans la fenêtre **Sources de données**.

## <a name="create-a-dataset-for-an-mdb-file"></a>Créer un jeu de données pour un fichier. mdb

Connectez-vous aux bases de données créées avec Access 2000-2003 à l’aide de la procédure suivante.

1. Ouvrez un Windows Forms ou un projet d’application WPF dans Visual Studio.

2. Dans le menu **affichage** , sélectionnez **autres**  >  **sources de données** Windows.

   ![Afficher d'autres sources de données Windows](../data-tools/media/viewdatasources.png)

3. Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.

    L' **Assistant Configuration de source de données** s’ouvre.

4. Sélectionnez **base de données** dans la page **choisir un type de source de données** , puis sélectionnez **suivant**.

5. Sélectionnez **DataSet** dans la page **choisir un modèle de base de données** , puis sélectionnez **suivant**.

6. Dans la page **Choisir votre connexion de données** , sélectionnez **Nouvelle connexion** pour configurer une nouvelle connexion de données.

7. Si la source de données n’est pas un **fichier de base de données Microsoft Access (OLE DB)** , sélectionnez **modifier** pour ouvrir la boîte de dialogue **modifier la source de données** et sélectionnez **fichier de base de données Microsoft Access** , puis cliquez sur **OK**.

8. Dans le **nom du fichier de base de données** , spécifiez le chemin d’accès et le nom du fichier *. mdb* auquel vous souhaitez vous connecter, puis sélectionnez **OK**.

   ![Ajouter une connexion à un fichier de base de données Access](../data-tools/media/add-connection-access-db.png)

9. Sélectionnez **suivant** dans la page **choisir votre connexion de données** .

10. Sélectionnez **suivant** dans la page **enregistrer la chaîne de connexion dans le fichier de configuration de l’application** .

11. Développez le nœud **tables** dans la page **choisir vos objets de base de données** .

12. Sélectionnez les tables ou les vues que vous souhaitez dans votre jeu de données, puis sélectionnez **Terminer**.

    Le jeu de données est ajouté à votre projet, et les tables et vues s’affichent dans la fenêtre **Sources de données**.

## <a name="next-steps"></a>Étapes suivantes

Le DataSet que vous venez de créer est disponible dans la fenêtre **sources de données** . Vous pouvez à présent effectuer l’une des tâches suivantes :

- Sélectionnez des éléments dans la fenêtre **sources de données** et faites-les glisser sur votre formulaire ou aire de conception (consultez [lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) ou [vue d’ensemble de la liaison de données WPF](/dotnet/desktop-wpf/data/data-binding-overview)).

- Ouvrez la source de données dans le **Concepteur de DataSet** pour ajouter ou modifier les objets qui composent le jeu de données.

- Ajoutez une logique de validation à l' <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> événement ou des tables de données dans le DataSet (consultez [valider des données dans des datasets](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Voir aussi

- [Ajouter des connexions](../data-tools/add-new-connections.md)
- [Vue d’ensemble de la liaison de données WPF](/dotnet/framework/wpf/data/data-binding-overview)
- [Liaison de données Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)
