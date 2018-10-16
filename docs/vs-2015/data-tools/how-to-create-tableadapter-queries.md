---
title: 'Comment : créer des requêtes TableAdapter | Microsoft Docs'
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
- TableAdapters, creating queries
- queries [Visual Studio], creating
- data [Visual Studio], TableAdapter queries
- queries [Visual Studio], TableAdapters
ms.assetid: df0cf4a5-e9cc-4de6-8b94-ce74fb7b2452
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: c4b800bcb70e41e1d80bf9a0a37d72f08f78c7a6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195544"
---
# <a name="how-to-create-tableadapter-queries"></a>Comment : créer des requêtes TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les requêtes TableAdapter sont des instructions SQL ou des procédures stockées que votre application peut s’exécuter sur une base de données.  
  
 Ajoutez autant de requêtes à un TableAdapter que nécessaire pour votre application. Les requêtes TableAdapter apparaissent en tant que méthodes sur un TableAdapter. Lorsque vous créez une requête appelée `FillByCity` qui prend un paramètre représentant la valeur de la ville, la requête est ajoutée au TableAdapter. Il est ajouté en tant qu’une méthode typée qui prend le type de paramètre en tant qu’argument approprié, dans ce cas, une chaîne représentant la valeur de la ville. Vous appelez la requête TableAdapter comme n’importe quelle méthode sur n’importe quel objet. Par exemple, le code suivant exécute la `FillByCity` requête et remplit le `Customers` table avec tous les clients avec une valeur de la ville de `Seattle`:  
  
 [!code-csharp[VbRaddataTableAdapters#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form1.cs#1)]
 [!code-vb[VbRaddataTableAdapters#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form1.vb#1)]  
  
 Requêtes TableAdapter peuvent remplir une table de données (`Fill` et `FillBy` requêtes) ou retourner de nouvelles tables de données remplis avec les données retournées par la requête (`GetData` et `GetDataBy` requêtes).  
  
 Vous pouvez ajouter des requêtes à des TableAdapters existants en exécutant la [modification des TableAdapters](../data-tools/editing-tableadapters.md). (Avec le bouton droit n’importe quel TableAdapter et choisissez **ajouter une requête**.)  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="create-a-query-in-the-dataset-designer"></a>Créer une requête dans le Concepteur de Dataset  
  
#### <a name="to-add-a-query-to-a-tableadapter-in-the-dataset-designer"></a>Pour ajouter une requête à un TableAdapter dans le Concepteur de Dataset  
  
1.  Ouvrez un dataset dans le **Concepteur de Dataset**. Pour plus d’informations, consultez [Comment : ouvrir un jeu de données dans le Concepteur de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Cliquez sur le TableAdapter souhaité, puis sélectionnez **ajouter une requête**.  
  
     - ou -  
  
3.  Faites glisser un **requête** à partir de la **jeu de données** onglet de la **boîte à outils** sur une table dans le concepteur.  
  
     Le **Assistant Configuration de requêtes TableAdapter** s’ouvre.  
  
4.  Terminez l’Assistant ; la requête est ajoutée au TableAdapter.  
  
## <a name="create-a-query-directly-on-a-form-in-your-windows-application"></a>Créer une requête directement sur un formulaire dans votre Application Windows  
 Si vous avez une instance d’un TableAdapter sur votre formulaire, vous pouvez ajouter une requête en utilisant le [boîte de dialogue Générateur de critères de recherche](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d), qui ajoute un <xref:System.Windows.Forms.ToolStrip> contrôle au formulaire qui accepte les paramètres d’entrée requis par la requête, ainsi qu’un bouton pour exécuter la requête.  
  
#### <a name="to-add-a-query-to-a-tableadapter-using-the-search-criteria-dialog-box"></a>Pour ajouter une requête à un TableAdapter à l’aide de la boîte de dialogue critères de recherche  
  
1.  Sélectionnez un TableAdapter dans la barre d’état du composant.  
  
2.  Cliquez sur la balise active du TableAdapter, puis choisissez **ajouter une requête**.  
  
3.  Fermer la boîte de dialogue et la requête est ajoutée au TableAdapter. Pour plus d’informations, consultez [boîte de dialogue Générateur de critères de recherche](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Comment : modifier des requêtes TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)   
 [Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md)   
 [Comment : établir une connexion à des données d’une base de données](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Comment : naviguer parmi les données avec le contrôle BindingNavigator Windows Forms](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)   
 [Procédure pas à pas : Affichage de données sur un formulaire Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Procédure pas à pas : création d’un TableAdapter avec plusieurs requêtes](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)