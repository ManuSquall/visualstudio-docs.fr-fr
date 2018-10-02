---
title: Afficher les données associées dans les applications WPF | Microsoft Docs
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
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c4068bcbf3ead7114013b93f02a784d682e5b4d5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505567"
---
# <a name="display-related-data-in-wpf-applications"></a>Afficher les données associées dans les applications WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [affichent les données connexes dans des applications WPF](https://docs.microsoft.com/visualstudio/data-tools/display-related-data-in-wpf-applications).  
  
  
Dans certaines applications, vous souhaiterez utiliser des données provenant de plusieurs tables ou entités qui sont liées entre eux dans une relation parent-enfant. Par exemple, vous souhaiterez peut-être afficher une grille qui montre les clients d’un `Customers` table. Lorsque l’utilisateur sélectionne un client spécifique, un autre élément grid affiche les commandes de ce client à partir d’un connexes `Orders` table.  
  
 Vous pouvez créer des contrôles liés aux données qui affichent les données associées en faisant glisser des éléments à partir de la **des Sources de données** fenêtre vers le Concepteur WPF.  
  
## <a name="to-create-controls-that-display-related-records"></a>Pour créer des contrôles qui affichent des enregistrements connexes  
  
1.  Sur le **données** menu, cliquez sur **afficher les Sources de données** pour ouvrir le **des Sources de données** fenêtre.  
  
2.  Cliquez sur **ajouter une nouvelle Source de données**, terminez la **Configuration de Source de données** Assistant.  
  
3.  Ouvrez le Concepteur WPF et vous assurer que le concepteur contient un conteneur qui est une cible de dépôt valide pour les éléments dans le **des Sources de données** fenêtre.  
  
     Pour plus d’informations sur les cibles de dépôt valides, consultez [WPF de lier des contrôles à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
4.  Dans le **des Sources de données** fenêtre, développez le nœud qui représente la table parente ou de l’objet dans la relation. La table parente ou l’objet est sur le côté « un » d’une relation un-à-plusieurs.  
  
5.  Faites glisser le nœud parent (ou tous les éléments individuels dans le nœud parent) de la **des Sources de données** fenêtre vers une cible de dépôt valides dans le concepteur.  
  
     Visual Studio génère le XAML qui crée des contrôles liés aux données pour chaque élément que vous faites glisser. Le XAML ajoute également un nouveau <xref:System.Windows.Data.CollectionViewSource> pour l’objet pour les ressources de la cible de déplacement ou la table parente. Pour certaines sources de données, Visual Studio génère également du code pour charger les données dans la table parente ou l’objet. Pour plus d’informations, consultez [WPF de lier des contrôles à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
6.  Dans le **des Sources de données** fenêtre, recherchez la table enfant connexe ou l’objet. Tables et objets enfants connexes s’affichent en tant que nœuds extensibles en bas de la liste du nœud parent de données.  
  
7.  Faites glisser le nœud enfant (ou tous les éléments individuels dans le nœud enfant) de la **des Sources de données** fenêtre vers une cible de dépôt valides dans le concepteur.  
  
     Visual Studio génère le XAML qui crée des contrôles liés aux données pour chacun des éléments que vous faites glisser. Le XAML ajoute également un nouveau <xref:System.Windows.Data.CollectionViewSource> pour l’objet pour les ressources de la cible de déplacement ou la table enfant. Cette nouvelle <xref:System.Windows.Data.CollectionViewSource> est lié à la propriété de la table parente ou l’objet que vous venez de faire glisser vers le concepteur. Pour certaines sources de données, Visual Studio génère également du code pour charger les données dans la table enfant ou l’objet.  
  
     La figure suivante illustre le connexes **commandes** table de la **clients** table dans un jeu de données dans le **Sources de données** fenêtre.  
  
     ![Fenêtre de Sources de données montrant la relation](../data-tools/media/datasources2.gif "DataSources2")  
  
## <a name="see-also"></a>Voir aussi  
 [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Créer des tables de recherche dans les applications WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [Procédure pas à pas : affichage de données connexes dans une application WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)

