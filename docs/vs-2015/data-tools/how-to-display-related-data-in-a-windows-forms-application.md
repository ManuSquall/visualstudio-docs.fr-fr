---
title: 'Comment : afficher des connexes à des données dans un Windows Forms Application | Microsoft Docs'
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
- Windows Forms, displaying data
- displaying data, related data
- related data, displaying
- displaying tables, related data
- data [Windows Forms], displaying
- displaying table data
- data [Windows Forms], related
- displaying data on forms, related data
- displaying table information
ms.assetid: 60b1f1ec-6257-42ab-83f0-06d54ed364fd
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: fc62789860cc10f5c410849936715a8ef82eae3f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506922"
---
# <a name="how-to-display-related-data-in-a-windows-forms-application"></a>Comment : afficher des données connexes dans une application Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez afficher les données associées en faisant glisser des éléments qui partagent le même nœud de la table principale à partir de la [fenêtre Sources de données](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) vers votre formulaire. Par exemple, si vous avez une données source qui a un `Customers` table et un connexes `Orders` table, vous pouvez voir les deux tables en tant que nœuds de niveau supérieur (dans l’arborescence de commandes) dans le **des Sources de données** fenêtre. Développez le `Customers` nœud afin que vous pouvez voir les colonnes, et vous remarquerez que la dernière colonne dans la liste est un nœud extensible représentant le `Orders` table. Ce nœud représente les commandes connexes d’un client. Cela signifie que si vous souhaitez créer un formulaire qui vous permet de sélectionner un client et afficher une liste des commandes de ce client, faites glisser les éléments que vous souhaitez afficher depuis cette hiérarchie unique.  
  
 ![Fenêtre de Sources de données montrant la relation](../data-tools/media/datasources2.gif "DataSources2")  
Création de contrôles liés aux données qui affichent des enregistrements connexes  
  
 ![lien vers la vidéo](../data-tools/media/playvideo.gif "PlayVideo") pour obtenir une version vidéo de cette rubrique, consultez [How do i : mise à jour des Tables associées](http://go.microsoft.com/fwlink/?LinkId=143527).  
  
### <a name="to-create-controls-that-display-related-records"></a>Pour créer des contrôles qui affichent des enregistrements connexes  
  
1.  Ouvrir votre formulaire dans le [Windows Forms Designer](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
2.  Ouvrez le **des Sources de données** fenêtre. Pour plus d’informations, consultez [Comment : ouvrir la fenêtre sources de données](../data-tools/how-to-open-the-data-sources-window.md).  
  
3.  Développez le nœud représentant la table parente dans la relation. (La table parente est la table sur le côté « un » d’une relation un-à-plusieurs.)  
  
4.  Faites glisser les éléments que vous souhaitez afficher à partir de la table parent dans la relation à partir de la **des Sources de données** fenêtre vers votre formulaire.  
  
5.  Les tables enfants connexes apparaissent sous forme de nœuds extensibles en bas de la liste des colonnes de la table parente. Faites glisser les éléments que vous souhaitez afficher depuis un tel nœud connexe vers votre formulaire.  
  
    > [!NOTE]
    >  Faire glisser un élément depuis un nœud de niveau supérieur crée un distinct non lié [composant BindingSource](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9) qui ne facilite pas la navigation dans les enregistrements associés. Pour lier des données connexes, vous devez sélectionner les tables à partir du même nœud hiérarchique.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures pas à pas de données](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Procédure pas à pas : Affichage de données sur un formulaire Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Vue d’ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)   
 [Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md)   
 [Comment : établir une connexion à des données d’une base de données](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Comment : naviguer parmi les données avec le contrôle BindingNavigator Windows Forms](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)