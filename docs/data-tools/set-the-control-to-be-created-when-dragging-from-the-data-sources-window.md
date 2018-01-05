---
title: "Définir le contrôle à créer lors du déplacement de la fenêtre Sources de données | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
caps.latest.revision: "31"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 5556a5d9a537684a8d1e73ee363b4c9ac8f6baa8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>Définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre Sources de données
Vous pouvez créer des contrôles liés aux données en faisant glisser des éléments depuis la **des Sources de données** fenêtre vers le Concepteur WPF ou le Concepteur Windows Forms. Chaque élément dans le **des Sources de données** fenêtre possède un contrôle par défaut qui est créé lorsque vous faites glisser vers le concepteur. Toutefois, vous pouvez choisir de créer un autre contrôle.  
  
## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>Définir les contrôles à créer pour les tables de données ou des objets  
Avant de faire glisser des éléments qui représentent des tables de données ou des objets à partir de la **des Sources de données** fenêtre, vous pouvez choisir d’afficher toutes les données dans un contrôle, ou pour afficher chaque colonne ou propriété dans un contrôle distinct.  
  
Dans ce contexte, le terme *objet* fait référence à un objet métier personnalisé, une entité (dans un Entity Data Model) ou un objet retourné par un service.  
  
### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>Pour définir les contrôles à créer pour les tables de données ou des objets  
  
1.  Assurez-vous que le Concepteur WPF ou le Concepteur Windows Forms est ouvert.  
  
2.  Dans le **des Sources de données** fenêtre, sélectionnez l’élément qui représente la table de données ou de l’objet à définir.  
  
3.  Cliquez sur le menu déroulant pour l’élément, puis cliquez sur un des éléments suivants dans le menu :  
  
    -   Pour afficher chaque champ de données dans un contrôle distinct, cliquez sur **détails**. Lorsque vous faites glisser l’élément de données vers le concepteur, cette action créera un contrôle lié aux données différent pour chaque colonne ou propriété de l’objet, ainsi que des étiquettes pour chaque contrôle ou de table de données parente.  
  
    -   Pour afficher toutes les données dans un seul contrôle, sélectionnez un autre contrôle dans la liste, telle que **DataGrid** ou **liste** dans une application WPF, ou **DataGridView** dans Windows Forms application.  
  
    La liste des contrôles disponibles dépend du concepteur que vous avez ouvert, la version du .NET Framework que votre projet cible, et si vous avez ajouté personnalisé de contrôles cette prise en charge de liaison de données à la **boîte à outils**. Si le contrôle que vous souhaitez créer n’est pas dans la liste des contrôles disponibles, vous pouvez ajouter le contrôle à la liste. Pour plus d’informations, consultez [ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
    Pour savoir comment créer un contrôle Windows Forms personnalisé qui peut être ajouté à la liste de contrôles pour les tables de données ou des objets dans le **des Sources de données** fenêtre, consultez [créer un contrôle utilisateur Windows Forms qui prend en charge des données complexes liaison](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).  
  
## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>Définir les contrôles à créer pour les colonnes de données ou des propriétés  
Avant de faire glisser un élément qui représente une colonne ou une propriété d’un objet à partir de la **des Sources de données** fenêtre vers le concepteur, vous pouvez définir le contrôle à créer.  
  
#### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>Pour définir les contrôles à créer pour des colonnes ou des propriétés  
  
1.  Assurez-vous que le Concepteur WPF ou le Concepteur Windows Forms est ouvert.  
  
2.  Dans le **des Sources de données** fenêtre, développez la table souhaitée, ou pour afficher ses colonnes ou les propriétés de l’objet.  
  
3.  Sélectionnez chaque colonne ou la propriété pour laquelle vous souhaitez définir le contrôle à créer.  
  
4.  Cliquez sur le menu déroulant de la colonne ou la propriété, puis sélectionnez le contrôle à créer lorsque vous faites glisser l’élément vers le concepteur.  
  
     La liste des contrôles disponibles dépend du concepteur que vous avez ouvert, la version du .NET Framework que votre projet cible, et des contrôles personnalisés qui prennent en charge de liaisons de données ont ajoutés à la **boîte à outils**. Si le contrôle que vous souhaitez créer est dans la liste des contrôles disponibles, vous pouvez ajouter le contrôle à la liste. Pour plus d’informations, consultez [ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
     Pour savoir comment créer un contrôle personnalisé qui peut être ajouté à la liste de contrôles pour les colonnes de données ou les propriétés dans le **des Sources de données** fenêtre, consultez [créer un contrôle utilisateur Windows Forms qui prend en charge la liaison de données simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).  
  
     Si vous ne souhaitez pas créer un contrôle pour la colonne ou propriété, sélectionnez **aucun** dans le menu déroulant. Cela est utile si vous souhaitez faire glisser la table parent ou l’objet vers le concepteur, mais vous ne souhaitez pas inclure la colonne ou propriété particulière.  
  
## <a name="see-also"></a>Voir aussi
[Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)