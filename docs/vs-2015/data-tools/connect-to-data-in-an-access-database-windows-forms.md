---
title: Se connecter aux données dans une base de données Access (Windows Forms) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4741dedb907bb88513147a98b916831abd965576
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207348"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Se connecter aux données dans une base de données Access (Windows Forms)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Vous pouvez vous connecter à une base de données Access (un fichier .mdf ou un fichier .accdb) à l’aide de Visual Studio. Une fois que vous définissez la connexion, les données apparaissent dans le **des Sources de données** fenêtre. De là, vous pouvez faire glisser des tables ou des vues sur vos formulaires. Si vous souhaitez comprendre comment le système de projet dans Visual Studio gère ces fichiers de base de données locale, consultez [Comment : gérer les fichiers de données Local dans votre projet](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour utiliser ces procédures, vous avez besoin d’un projet d’application Windows Forms et une base de données Access (fichier .accdb) ou une base de données Access 2000-2003 (fichier .mdb). Suivez la procédure qui correspond à votre type de fichier.  
  
## <a name="creating-the-dataset-for-an-accdb-file"></a>Créer le jeu de données pour un fichier .accdb  
 Vous pouvez vous connecter aux bases de données créés via Access 2013, Office 365, Access 2010 ou Access 2007 à l’aide de la procédure suivante.  
  
#### <a name="to-create-the-dataset"></a>Pour créer le groupe de données  
  
1.  Ouvrez l’application Windows Forms à laquelle vous souhaitez vous connecter des données.  
  
2.  Sur le **vue** menu, sélectionnez **Windows autres** > **des Sources de données**.  
  
     ![Afficher d’autres Sources de données Windows](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3.  Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.  
  
     ![Ajouter une nouvelle Source de données](../data-tools/media/dataaddnewdatasource.png "dataAddNewDataSource")  
  
4.  Sélectionnez **base de données** sur le **choisir un Type de Source de données** page, puis sélectionnez **suivant**.  
  
5.  Sélectionnez **Dataset** sur le **choisir un modèle de base de données** page, puis sélectionnez **suivant**.  
  
6.  Sur le **choisir votre connexion de données** page, sélectionnez **nouvelle connexion** pour configurer une nouvelle connexion de données.  
  
7.  Modifier le **source de données** à **fournisseur de données .NET Framework pour OLE DB**.  
  
     ![Modifier le fournisseur de données OLE DB](../data-tools/media/datachangedatasourceoledb.png "dataChangeDataSourceOLEDB")  
  
    > [!IMPORTANT]
    >  Bien qu’une source de données de **du fichier de base de données Microsoft Access (OLE DB)** peut sembler être le bon choix, vous utilisez ce type de source de données uniquement pour les fichiers de base de données .mdb.  
  
8.  Dans **fournisseur OLE DB**, sélectionnez **Microsoft Office 12.0 Access Database Engine fournisseur OLE DB**.  
  
     ![OLE DB fournisseur Microsoft Office Access 12.0](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")  
  
9. Dans **serveur ou nom de fichier**, spécifiez le chemin d’accès et le nom du fichier .accdb auquel vous souhaitez vous connecter, puis sélectionnez **OK**.  
  
    > [!NOTE]
    >  Si le fichier de base de données a un nom d’utilisateur et le mot de passe, indiquez-les avant de sélectionner **OK**.  
  
10. Sélectionnez **suivant** sur le **choisir votre connexion de données** page.  
  
11. Sélectionnez **suivant** sur le **enregistrer la chaîne de connexion dans le fichier de Configuration de l’Application** page.  
  
12. Développez le **Tables** nœud sur le **choisir vos objets de base de données** page.  
  
13. Sélectionnez les tables ou des vues de votre choix dans votre jeu de données, puis sélectionnez **Terminer**.  
  
     Le jeu de données est ajouté à votre projet et les tables et vues s’affichent dans le **des Sources de données** fenêtre.  
  
## <a name="creating-the-dataset-for-an-mdb-file"></a>Créer le jeu de données pour un fichier .mdb  
 Vous créez le jeu de données en exécutant la **Assistant de Configuration de Source de données**.  
  
#### <a name="to-create-the-dataset"></a>Pour créer le groupe de données  
  
1.  Ouvrez l’application Windows Forms à laquelle vous souhaitez vous connecter des données.  
  
2.  Sur le **vue** menu, sélectionnez **Windows autres** > **des Sources de données**.  
  
     ![Afficher d’autres Sources de données Windows](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3.  Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.  
  
4.  Sélectionnez **base de données** sur le **choisir un Type de Source de données** page, puis sélectionnez **suivant**.  
  
5.  Sélectionnez **Dataset** sur le **choisir un modèle de base de données** page, puis sélectionnez **suivant**.  
  
6.  Sur le **choisir votre connexion de données** page, sélectionnez **nouvelle connexion** pour configurer une nouvelle connexion de données.  
  
7.  Si la source de données n’est pas **du fichier de base de données Microsoft Access (OLE DB)**, sélectionnez **modification** pour ouvrir le **modifier la Source de données** boîte de dialogue et sélectionnez **Microsoft Accéder au fichier de base de données**, puis sélectionnez **OK**.  
  
8.  Dans le **nom de fichier de base de données**, spécifiez le chemin d’accès et le nom du fichier .mdb auquel vous souhaitez vous connecter, puis sélectionnez **OK**.  
  
     ![Ajouter le fichier de connexion de base de données Access](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")  
  
9. Sélectionnez **suivant** sur le **choisir votre connexion de données** page.  
  
10. Sélectionnez **suivant** sur le **enregistrer la chaîne de connexion dans le fichier de Configuration de l’Application** page.  
  
11. Développez le **Tables** nœud sur le **choisir vos objets de base de données** page.  
  
12. Sélectionnez les tables ou des vues de votre choix dans votre jeu de données, puis sélectionnez **Terminer**.  
  
     Le jeu de données est ajouté à votre projet et les tables et vues s’affichent dans le **des Sources de données** fenêtre.  
  
## <a name="security"></a>Sécurité  
 Le stockage d'informations sensibles (telles qu'un mot de passe) peut affecter la sécurité de votre application. L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données. Pour plus d’informations, consultez [Protection des informations de connexion](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Le jeu de données que vous venez de créer est maintenant disponible dans le **des Sources de données** fenêtre. Vous pouvez maintenant effectuer les tâches suivantes :  
  
-   Sélectionnez des éléments dans le **des Sources de données** fenêtre et faites-les glisser jusqu'à votre formulaire (voir [lier les formulaires Windows contrôle aux données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).  
  
-   Ouvrez la source de données dans le [Concepteur de Dataset](../data-tools/creating-and-editing-typed-datasets.md) pour ajouter ou modifier les objets qui composent le jeu de données.  
  
-   Ajouter une logique de validation pour le <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging> événement les tables de données dans le jeu de données (voir [valider des données dans les jeux de données](../data-tools/validate-data-in-datasets.md)).  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre Application à recevoir des données](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Récupération de données dans votre Application](../data-tools/fetching-data-into-your-application.md)   
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre Application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [L’enregistrement des données](../data-tools/saving-data.md)   
 [Procédures pas à pas de données](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)

