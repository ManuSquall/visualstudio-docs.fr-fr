---
title: 'Comment : se connecter aux données dans une base de données | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
- data sources, databases
- data [Visual Studio], connecting to databases
- data sources, creating
- database connections
ms.assetid: 6c56e54e-8834-4297-85aa-cc1a443ba556
caps.latest.revision: 55
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 72b278305995e2edb86e612e0c5c3789c8ce756a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495729"
---
# <a name="how-to-connect-to-data-in-a-database"></a>Comment : établir une connexion à des données d'une base de données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser Visual Studio pour connecter votre application à une base de données. Après avoir créé la connexion de données, Visual Studio génère un modèle de données que votre application utilise pour interagir avec les données figurant dans la base de données. Les objets dans le modèle de données s’affichent dans le [fenêtre Sources de données](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992). Vous pouvez ensuite créer des contrôles liés aux données en faisant glisser des éléments à partir de la **fenêtre Sources de données** à une aire de conception. Pour plus d’informations, consultez [lier des contrôles aux données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Cette rubrique fournit des instructions pour la connexion à une base de données et la création des types de modèles de données suivants :  
  
-   Groupe de données  
  
-   EDM (Entity Data Model)  
  
> [!NOTE]
>  Vous pouvez également utiliser Visual Studio pour créer des classes LINQ to SQL à partir d'une base de données. Toutefois, les classes LINQ to SQL n’apparaissent pas dans le **des Sources de données** fenêtre et par conséquent ne peut pas être déplacé directement vers un concepteur pour créer des contrôles liés aux données. Pour plus d’informations sur la création de LINQ aux classes SQL à partir d’une base de données, consultez [Comment : créer des classes LINQ to SQL mappées aux tables et vues (Concepteur O/R)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
##  <a name="dataset"></a> Connexion à une base de données et la création d’un jeu de données  
 Lorsque vous créez un groupe de données basé sur une base de données, Visual Studio crée un ensemble de classes qui représente une vue programmable des données. La classe principale est appelée un *dataset typé*. Le dataset typé contient des objets de table de données qui représentent des tables dans la base de données. Pour plus d’informations sur les datasets typés, consultez [outils de Dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
 Après avoir créé un groupe de données (dataset), vous pouvez créer des contrôles WPF ou des contrôles Windows Forms liés aux données en faisant glisser des objets Dataset de la fenêtre Sources de données vers le Concepteur WPF ou le Concepteur Windows Forms.  
  
#### <a name="to-connect-your-application-to-a-database-and-create-a-dataset"></a>Pour connecter votre application à une base de données et créer un groupe de données  
  
1.  Ouvrez un projet existant dans Visual Studio ou créez un nouveau projet.  
  
2.  Dans le menu **Données** , cliquez sur **Ajouter une nouvelle source de données**.  
  
     Le **Assistant de Configuration de Source de données** s’ouvre.  
  
3.  Sur le **choisir un Type de Source de données** page, sélectionnez **base de données**, puis cliquez sur **suivant**.  
  
4.  Sur le **choisir un modèle de base de données** page, sélectionnez **Dataset**, puis cliquez sur **suivant**.  
  
5.  Sur le **choisir votre connexion de données** page, sélectionnez une connexion de données dans la liste des connexions disponibles, puis sur **suivant**.  
  
     Si votre connexion de données souhaitée n’est pas disponible, créez une nouvelle connexion en suivant les étapes de [création d’une nouvelle connexion de base de données](#CreatingDataConnection).  
  
6.  Sur le **enregistrer la chaîne de connexion dans le fichier de configuration** page, désactivez éventuellement la **Oui, enregistrer la connexion en tant que** case à cocher si vous souhaitez enregistrer la chaîne de connexion directement dans compilé application. Par défaut, la connexion est enregistrée dans le fichier de configuration de l'application. Pour plus d’informations, consultez [Comment : enregistrer et modifier des chaînes de connexion](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
7.  Sur le **choisir vos objets de base de données** page, sélectionnez les objets de base de données que vous utiliserez dans votre application. Vous avez également la possibilité de remplacer la valeur par défaut **nom du DataSet**.  
  
8.  Cliquez sur **Terminer**. Le jeu de données que vous venez de créer est maintenant disponible dans le **des Sources de données** fenêtre.  
  
    > [!NOTE]
    >  Si le **des Sources de données** fenêtre n’est pas ouverte, cliquez sur **afficher les Sources de données** sur le **données** menu pour ouvrir la fenêtre.  
  
9. Vous pouvez maintenant faire glisser des éléments à partir de la **des Sources de données** fenêtre vers le Concepteur WPF, le Concepteur Windows Forms, ou le [Component Designer](http://msdn.microsoft.com/library/61a3a450-5b15-465e-bd9a-72a6c8c2b282) pour créer des contrôles liés aux données. Pour plus d’informations, consultez [lier des contrôles aux données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
##  <a name="edm"></a> Connexion à la base de données et la création d’un Entity Data Model  
 Lorsque vous créez un Entity Data Model basé sur une base de données, Visual Studio crée un ensemble de classes qui représente une vue programmable des données. Pour plus d’informations sur les Entity Data Models et ADO.NET Entity Framework, consultez [présentation d’Entity Framework](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).  
  
 Après avoir créé un Entity Data Model, vous pouvez créer des contrôles WPF liés aux données en faisant glisser des objets d'entité de la fenêtre Sources de données vers le Concepteur WPF.  
  
#### <a name="to-connect-your-application-to-a-database-and-create-an-entity-data-model"></a>Pour connecter votre application à une base de données et créer un Entity Data Model  
  
1.  Ouvrez un projet existant dans Visual Studio ou créez un nouveau projet.  
  
2.  Suivez les étapes de la **Assistant Entity Data Model** pour vous connecter à une base de données et spécifier le contenu du modèle. Pour plus d’informations, consultez [Comment : créer un fichier .edmx](http://msdn.microsoft.com/en-us/beb8189e-e51c-4051-839c-9902c224abf2).  
  
3.  Après avoir terminé la **Assistant Entity Data Model**, l’Entity Data Model que vous avez créé s’ouvre dans l’Entity Data Model Designer, et les objets de données sont désormais disponibles dans le **des Sources de données** fenêtre.  
  
    > [!NOTE]
    >  Si le **des Sources de données** fenêtre n’est pas ouverte, cliquez sur **afficher les Sources de données** sur le **données** menu pour ouvrir la fenêtre.  
  
4.  Si le Concepteur WPF est ouvert, vous pouvez maintenant faire glisser des éléments à partir de la **des Sources de données** fenêtre vers le concepteur pour créer des contrôles qui sont liés à l’Entity Data Model. Pour plus d’informations, consultez [WPF de lier des contrôles à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md).  
  
     Si le Concepteur Windows Forms est ouvert, vous ne pouvez pas faire glisser des éléments de la **des Sources de données** vers le concepteur. Pour créer des contrôles liés à l'Entity Data Model, vous devez générer le projet, ajouter une nouvelle source de données d'objet basée sur l'Entity Data Model, puis faire glisser ces objets vers le concepteur.  
  
##  <a name="CreatingDataConnection"></a> Création d’une nouvelle connexion de base de données  
 Lorsque vous utilisez le **Assistant de Configuration de Source de données**ou **Assistant Entity Data Model**, vous devez spécifier une connexion à la base de données que vous souhaitez utiliser. Si vous ne disposez pas encore de connexion à la base de données, exécutez les étapes suivantes pour créer la connexion.  
  
 Ces instructions supposent que vous avez déjà commencé la **Assistant de Configuration de Source de données** ou **Assistant Entity Data Model** comme décrit dans [connexion à la base de données et la création d’un jeu de données ](#dataset) et [connexion à la base de données et la création d’un Entity Data Model](#edm).  
  
#### <a name="to-create-a-new-database-connection"></a>Pour créer une nouvelle connexion à une base de données  
  
1.  Sur le **choisir votre connexion de données** page de la **Assistant de Configuration de Source de données** ou **Assistant Entity Data Model**, cliquez sur **unenouvelleconnexion**.  
  
     L'une des actions suivantes se produit :  
  
    -   Si vous avez déjà créé une connexion de données dans Visual Studio, le **ajouter une connexion** boîte de dialogue s’ouvre.  
  
    -   Si c’est la première connexion de données que vous avez créé dans Visual Studio, le **choisir la Source de données** boîte de dialogue s’affiche. Sélectionnez le type de base de données que vous souhaitez vous connecter à, puis cliquez sur **OK** pour afficher le **ajouter une connexion** boîte de dialogue.  
  
2.  Dans le **ajouter une connexion** boîte de dialogue, entrez les informations demandées. Le **ajouter une connexion** boîte de dialogue est différente pour chaque type de fournisseur de données.  
  
    > [!NOTE]
    >  Si le texte sélectionné **source de données** dans le **ajouter une connexion** boîte de dialogue n’est pas la source de données que vous souhaitez vous connecter, cliquez sur **modification** pour ouvrir le **données modifiées Source** boîte de dialogue zone, puis choisissez une autre source de données.  
  
3.  Dans le **ajouter une connexion** boîte de dialogue, cliquez sur **OK**.  
  
     Vous revenez à la **choisir votre connexion de données** page de la **Assistant de Configuration de Source de données** ou **Assistant Entity Data Model**.  
  
4.  Sur le **choisir votre connexion de données** page, assurez-vous que la connexion de données est sélectionnée, puis sur **suivant**.  
  
5.  Complétez les étapes restantes le **Assistant de Configuration de Source de données** ou **Assistant Entity Data Model**.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Le stockage d'informations sensibles (telles qu'un mot de passe) peut affecter la sécurité de votre application. L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données. Pour plus d’informations, consultez [Protection des informations de connexion](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md)   
 [Procédures pas à pas de données](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Connexion à une source de données](http://msdn.microsoft.com/library/9abc3f92-1be3-4e1a-b360-762dc689650e)