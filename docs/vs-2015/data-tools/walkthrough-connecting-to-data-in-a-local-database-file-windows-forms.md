---
title: 'Procédure pas à pas : Connexion aux données dans un fichier de base de données locale (Windows Forms) | Microsoft Docs'
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
- local data, SQL Express
- SQL Express, walkthroughs
- SQL Express, connecting
- data [Visual Studio], local
- data [Visual Studio], connecting to SQL Express
ms.assetid: 5e16b7da-3fdc-4e69-bdb4-e8e700481811
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 71898c88a8d7a1d4a119a7e7a932e295ae12eb34
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176161"
---
# <a name="walkthrough-connecting-to-data-in-a-local-database-file-windows-forms"></a>Procédure pas à pas : connexion à des données dans un fichier de base de données local (Windows Forms)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez rapidement et facilement afficher des données à partir d'un fichier de base de données local dans votre application en créant un jeu de données et en ajoutant des contrôles liés aux données à votre application. Dans cette procédure pas à pas, vous afficherez des données à partir du fichier de base de données locale que vous avez créé en suivant les étapes décrites dans [créer une base de données SQL à l’aide d’un concepteur](../data-tools/create-a-sql-database-by-using-a-designer.md). Après avoir créé un projet Windows Forms, vous vous connecterez à cette base de données et spécifierez que les données de la table Customers apparaissent dans une grille de données sur le formulaire de l'application.  
  
 Lorsque vous créez une base de données dans Visual Studio 2013, le moteur SQL Server Express LocalDB permet d'accéder à un fichier de base de données (.mdf) dans SQL Server 2012. Dans les versions antérieures de Visual Studio, le moteur SQL Server Express est utilisé pour accéder à un fichier de base de données (.mdf). Consultez [vue d’ensemble des données locales](../data-tools/local-data-overview.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
 Cette procédure pas à pas comprend les tâches suivantes :  
  
-   [Création et configuration d’un jeu de données](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_CreateDataset)  
  
-   [Ajout de contrôles liés aux données](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_AddCtrls)  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure pas à pas, vous devez accéder à la base de données SampleDatabase.mdf que vous créez en effectuant [créer une base de données SQL à l’aide d’un concepteur](../data-tools/create-a-sql-database-by-using-a-designer.md).  
  
##  <a name="BKMK_CreateDataset"></a> Création et configuration d’un jeu de données  
  
#### <a name="to-create-and-configure-a-dataset"></a>Pour créer et configurer un jeu de données  
  
1.  Créez un projet Windows Forms et nommez-le **ConnectLocalData**.  
  
     Consultez [les Applications clientes](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
2.  Si le **des Sources de données** fenêtre n’est pas visible, appuyez sur les touches Alt-Maj-D ou, dans la barre de menus, choisissez **vue**, **Windows autres**, **afficher les Sources de données**.  
  
3.  Dans le **des Sources de données** fenêtre, choisissez le **ajouter une nouvelle Source de données** lien.  
  
     Dans le **Assistant de Configuration de Source de données**, choisissez le **suivant** deux fois pour accepter les paramètres par défaut.  
  
4.  Sur le **choisir votre connexion de données** page, choisissez le **nouvelle connexion** bouton.  
  
     Le **choisir la Source de données** boîte de dialogue s’affiche.  
  
5.  Dans le **source de données** , choisissez **fichier de base de données Microsoft SQL Server**, puis choisissez le **continuer** bouton.  
  
     Le **ajouter une connexion** boîte de dialogue s’affiche.  
  
6.  Dans le **nom de fichier de base de données** , spécifiez le fichier que vous avez créé en effectuant [créer une base de données SQL à l’aide d’un concepteur](../data-tools/create-a-sql-database-by-using-a-designer.md), ou choisissez le **Parcourir** bouton, puis recherchez Ce fichier.  
  
     Par défaut, le fichier est dans les utilisateurs\\*Votre_compte*\Documents\Visual Studio *Version*\Projects\SampleDatabaseWalkthrough\SampleDatabaseWalkthrough.  
  
7.  Sous **ouvrez une session sur le serveur**, acceptez les valeurs par défaut, choisissez le **OK** bouton, puis choisissez le **suivant** bouton.  
  
    > [!NOTE]
    >  Lorsque vous connectez un fichier de base de données locale, vous pouvez créer une copie de la base de données dans votre projet ou vous connecter au fichier de base de données existant dans son emplacement actuel. Consultez [Comment : gérer des fichiers de données locaux dans votre projet](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
8.  Dans la boîte de dialogue qui s’affiche, choisissez **Oui** pour copier le fichier de base de données à votre projet.  
  
9. Sur le **enregistrer la chaîne de connexion au fichier de Configuration de l’Application** page, choisissez le **suivant** bouton.  
  
10. Sur le **choisir vos objets de base de données** page, développez le **Tables** nœud, sélectionnez le **clients** et **commandes** cases à cocher, puis Choisissez le **Terminer** bouton.  
  
     Le **SampleDatabaseDataSet** est ajouté à votre projet et le **clients** et **commandes** tables apparaissent dans le **des Sources de données** fenêtre.  
  
##  <a name="BKMK_AddCtrls"></a> Ajout de contrôles liés aux données  
  
#### <a name="to-add-data-bound-controls"></a>Pour ajouter des contrôles liés aux données  
  
1.  Déplacez le **clients** nœud à partir de la **des Sources de données** fenêtre sur **Form1**.  
  
     Un <xref:System.Windows.Forms.DataGridView> et une barre d'outils (<xref:System.Windows.Forms.BindingNavigator>) pour parcourir les enregistrements apparaissent sur le formulaire. Un [SampleDatabaseDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état du composant.  
  
2.  Pour exécuter l'application et afficher les données que vous avez ajoutées dans la procédure précédente, appuyez sur la touche F5.  
  
3.  Cliquez sur l’icône jaune d’ajout (![bouton Ajouter dans un Windows Form](../data-tools/media/addrecord.png "AddRecord")), ajoutez un enregistrement de client, puis enregistrez vos modifications en choisissant l’icône de disque (![bouton Enregistrer dans un Windows Form](../data-tools/media/saveinwf.png "SaveInWF")).  
  
4.  Supprimer l’enregistrement que vous venez de créer en le sélectionnant et en choisissant l’icône rouge de suppression (![bouton Supprimer dans un Windows Form](../data-tools/media/deleterecord.png "DeleteRecord")).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous pouvez créer ou modifier des objets dans le jeu de données si vous ouvrez la source de données dans le [création et modification de données typés](../data-tools/creating-and-editing-typed-datasets.md). Vous pouvez aussi ajouter une logique de validation aux événements <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging> des tables de données du jeu de données. Consultez [valider des données dans les jeux de données](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des données locales](../data-tools/local-data-overview.md)   
 [Comment : gérer des fichiers de données locaux dans votre projet](../data-tools/how-to-manage-local-data-files-in-your-project.md)   
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre Application à recevoir des données](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Récupération de données dans votre Application](../data-tools/fetching-data-into-your-application.md)   
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre Application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Enregistrer des données](../data-tools/saving-data.md)