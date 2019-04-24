---
title: Afficher les données associées dans les applications WPF | Microsoft Docs
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
manager: jillfra
ms.openlocfilehash: e8a7bd540f5c8a99145b892d080d8cb54e57d968
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061175"
---
# <a name="display-related-data-in-wpf-applications"></a>Afficher des données associées dans des applications WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans certaines applications, vous souhaiterez utiliser des données provenant de plusieurs tables ou entités qui sont liées entre eux dans une relation parent-enfant. Par exemple, vous souhaiterez peut-être afficher une grille qui montre les clients d’un `Customers` table. Lorsque l’utilisateur sélectionne un client spécifique, un autre élément grid affiche les commandes de ce client à partir d’un connexes `Orders` table.  
  
 Vous pouvez créer des contrôles liés aux données qui affichent les données associées en faisant glisser des éléments à partir de la **des Sources de données** fenêtre vers le Concepteur WPF.  
  
## <a name="to-create-controls-that-display-related-records"></a>Pour créer des contrôles qui affichent des enregistrements connexes  
  
1. Dans le menu **Données**, cliquez sur **Afficher les sources de données** pour ouvrir la fenêtre **Sources de données**.  
  
2. Cliquez sur **Ajouter une nouvelle source de données** et suivez les étapes de l’Assistant **Configuration de source de données**.  
  
3. Ouvrez le Concepteur WPF et vous assurer que le concepteur contient un conteneur qui est une cible de dépôt valide pour les éléments dans le **des Sources de données** fenêtre.  
  
     Pour plus d’informations sur les cibles de dépôt valides, consultez [WPF de lier des contrôles à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
4. Dans le **des Sources de données** fenêtre, développez le nœud qui représente la table parente ou de l’objet dans la relation. La table parente ou l’objet est sur le côté « un » d’une relation un-à-plusieurs.  
  
5. Faites glisser le nœud parent (ou tous les éléments individuels dans le nœud parent) de la **des Sources de données** fenêtre vers une cible de dépôt valides dans le concepteur.  
  
     Visual Studio génère le XAML qui crée des contrôles liés aux données pour chaque élément que vous faites glisser. Le XAML ajoute également un nouveau <xref:System.Windows.Data.CollectionViewSource> pour l’objet pour les ressources de la cible de déplacement ou la table parente. Pour certaines sources de données, Visual Studio génère également du code pour charger les données dans la table parente ou l’objet. Pour plus d’informations, consultez [WPF de lier des contrôles à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
6. Dans le **des Sources de données** fenêtre, recherchez la table enfant connexe ou l’objet. Tables et objets enfants connexes s’affichent en tant que nœuds extensibles en bas de la liste du nœud parent de données.  
  
7. Faites glisser le nœud enfant (ou tous les éléments individuels dans le nœud enfant) de la **des Sources de données** fenêtre vers une cible de dépôt valides dans le concepteur.  
  
     Visual Studio génère le XAML qui crée des contrôles liés aux données pour chacun des éléments que vous faites glisser. Le XAML ajoute également un nouveau <xref:System.Windows.Data.CollectionViewSource> pour l’objet pour les ressources de la cible de déplacement ou la table enfant. Cette nouvelle <xref:System.Windows.Data.CollectionViewSource> est lié à la propriété de la table parente ou l’objet que vous venez de faire glisser vers le concepteur. Pour certaines sources de données, Visual Studio génère également du code pour charger les données dans la table enfant ou l’objet.  
  
     La figure suivante illustre le connexes **commandes** table de la **clients** table dans un jeu de données dans le **Sources de données** fenêtre.  
  
     ![Fenêtre de Sources de données montrant la relation](../data-tools/media/datasources2.gif "DataSources2")  
  
## <a name="see-also"></a>Voir aussi  
 [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Créer des tables de recherche dans les applications WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [Procédure pas à pas : Affichage de données liées dans une Application WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
