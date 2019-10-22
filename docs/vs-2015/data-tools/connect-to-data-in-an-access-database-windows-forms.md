---
title: Se connecter aux données d’une base de données Access (Windows Forms) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8426e9fcaa29bef36b6701c78d622f6f42fd1171
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651142"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Se connecter à des données dans une base de données Access (Windows Forms)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez vous connecter à une base de données Access (fichier. mdf ou. accdb) à l’aide de Visual Studio. Après avoir défini la connexion, les données s’affichent dans la fenêtre **Sources de données**. De là, vous pouvez faire glisser des tables ou des vues sur vos formulaires.

## <a name="prerequisites"></a>Configuration requise
 Pour utiliser ces procédures, vous avez besoin d’un projet d’application Windows Forms et d’une base de données Access (fichier. accdb) ou d’une base de données Access 2000-2003 (fichier. mdb). Suivez la procédure qui correspond à votre type de fichier.

## <a name="creating-the-dataset-for-an-accdb-file"></a>Création du jeu de données pour un fichier .accdb
 Vous pouvez vous connecter aux bases de données créées via Access 2013, Office 365, Access 2010 ou Access 2007 à l’aide de la procédure suivante.

#### <a name="to-create-the-dataset"></a>Pour créer le groupe de données

1. Ouvrez l’application Windows Forms à laquelle vous voulez connecter des données.

2. Dans le menu **affichage** , sélectionnez **autres** Sources de**données**Windows  > .

     ![Afficher les autres sources de données Windows](../data-tools/media/viewdatasources.png "ViewDataSources")

3. Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.

     ![Ajouter une nouvelle source de données](../data-tools/media/dataaddnewdatasource.png "dataAddNewDataSource")

4. Sélectionnez **base de données** dans la page **choisir un type de source de données** , puis sélectionnez **suivant**.

5. Sélectionnez **DataSet** dans la page **choisir un modèle de base de données** , puis sélectionnez **suivant**.

6. Dans la page **Choisir votre connexion de données**, sélectionnez **Nouvelle connexion** pour configurer une nouvelle connexion de données.

7. Modifiez la **source de données** en **.NET Framework fournisseur de données pour OLE DB**.

     ![Remplacez Fournisseur de données par OLE DB](../data-tools/media/datachangedatasourceoledb.png "dataChangeDataSourceOLEDB")

    > [!IMPORTANT]
    > Bien qu’une source de données du **fichier de base de données Microsoft Access (OLE DB)** puisse sembler le bon choix, vous utilisez ce type de source de données uniquement pour les fichiers de base de données. mdb.

8. Dans **OLE DB fournisseur**, sélectionnez **Microsoft Office accès 12,0 moteur de base de données OLE DB fournisseur**.

     ![OLE DB fournisseur Microsoft Office accès 12,0](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")

9. Dans **nom du serveur ou du fichier**, spécifiez le chemin d’accès et le nom du fichier. accdb auquel vous souhaitez vous connecter, puis sélectionnez **OK**.

    > [!NOTE]
    > Si le fichier de base de données a un nom d’utilisateur et un mot de passe, spécifiez-les avant de sélectionner **OK**.

10. Sélectionnez **suivant** dans la page **choisir votre connexion de données** .

11. Sélectionnez **suivant** dans la page **enregistrer la chaîne de connexion dans le fichier de configuration de l’application** .

12. Développez le nœud **Tables** dans la page **Choisir vos objets de base de données**.

13. Sélectionnez les tables ou les vues que vous souhaitez dans votre jeu de données, puis sélectionnez **Terminer**.

     Le jeu de données est ajouté à votre projet, et les tables et vues s’affichent dans la fenêtre **Sources de données**.

## <a name="creating-the-dataset-for-an-mdb-file"></a>Création du jeu de données pour un fichier. mdb
 Pour créer le jeu de données, exécutez l’**Assistant Configuration de source de données**.

#### <a name="to-create-the-dataset"></a>Pour créer le groupe de données

1. Ouvrez l’application Windows Forms à laquelle vous voulez connecter des données.

2. Dans le menu **affichage** , sélectionnez **autres** Sources de**données**Windows  > .

     ![Afficher les autres sources de données Windows](../data-tools/media/viewdatasources.png "ViewDataSources")

3. Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.

4. Sélectionnez **base de données** dans la page **choisir un type de source de données** , puis sélectionnez **suivant**.

5. Sélectionnez **DataSet** dans la page **choisir un modèle de base de données** , puis sélectionnez **suivant**.

6. Dans la page **Choisir votre connexion de données**, sélectionnez **Nouvelle connexion** pour configurer une nouvelle connexion de données.

7. Si la source de données n’est pas un **fichier de base de données Microsoft Access (OLE DB)** , sélectionnez **modifier** pour ouvrir la boîte de dialogue **modifier la source de données** et sélectionnez **fichier de base de données Microsoft Access**, puis cliquez sur **OK**.

8. Dans le **nom du fichier de base de données**, spécifiez le chemin d’accès et le nom du fichier. mdb auquel vous souhaitez vous connecter, puis sélectionnez **OK**.

     ![Ajouter un fichier de base de données d’accès à la connexion](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")

9. Sélectionnez **suivant** dans la page **choisir votre connexion de données** .

10. Sélectionnez **suivant** dans la page **enregistrer la chaîne de connexion dans le fichier de configuration de l’application** .

11. Développez le nœud **Tables** dans la page **Choisir vos objets de base de données**.

12. Sélectionnez les tables ou les vues que vous souhaitez dans votre jeu de données, puis sélectionnez **Terminer**.

     Le jeu de données est ajouté à votre projet, et les tables et vues s’affichent dans la fenêtre **Sources de données**.

## <a name="security"></a>Sécurité
 Le stockage d'informations sensibles (telles qu'un mot de passe) peut affecter la sécurité de votre application. L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données. Pour plus d’informations, consultez [Protection des informations de connexion](https://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).

## <a name="next-steps"></a>Étapes suivantes
 Le DataSet que vous venez de créer est maintenant disponible dans la fenêtre **sources de données** . Vous pouvez à présent effectuer l’une des tâches suivantes :

- Sélectionnez des éléments dans la fenêtre **sources de données** et faites-les glisser sur votre formulaire (consultez [lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).

- Ouvrez la source de données dans le Concepteur de DataSet pour ajouter ou modifier les objets qui composent le DataSet.

- Ajoutez une logique de validation au <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging> événement des tables de données dans le DataSet (consultez [valider des données dans des datasets](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Voir aussi

 [Préparation de votre application pour recevoir des](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) [contrôles de liaison de données à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md) [validation](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e) des données de données [procédures pas à pas](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)