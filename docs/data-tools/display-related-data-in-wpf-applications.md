---
title: Afficher des données associées dans des applications WPF
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6ab1301e421f8326cf4cdda97556ecb19e394c29
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586677"
---
# <a name="display-related-data-in-wpf-applications"></a>Afficher des données associées dans des applications WPF

Dans certaines applications, vous souhaiterez peut-être utiliser des données provenant de plusieurs tables ou entités qui sont liées entre elles dans une relation parent-enfant. Par exemple, vous souhaiterez peut-être afficher une grille qui affiche les clients d’une table `Customers`. Lorsque l’utilisateur sélectionne un client spécifique, une autre grille affiche les commandes de ce client à partir d’une table de `Orders` associée.

Vous pouvez créer des contrôles liés aux données qui affichent les données associées en faisant glisser des éléments depuis la fenêtre **sources de données** vers le Concepteur WPF.

## <a name="to-create-controls-that-display-related-records"></a>Pour créer des contrôles qui affichent des enregistrements connexes

1. Dans le menu **Données**, cliquez sur **Afficher les sources de données** pour ouvrir la fenêtre **Sources de données**.

2. Cliquez sur **Ajouter une nouvelle source de données** et suivez les étapes de l’Assistant **Configuration de source de données**.

3. Ouvrez le Concepteur WPF et assurez-vous que le concepteur contient un conteneur qui est une cible de dépôt valide pour les éléments de la fenêtre **sources de données** .

     Pour plus d’informations sur les cibles de dépôt valides, consultez [lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

4. Dans la fenêtre **sources de données** , développez le nœud qui représente la table ou l’objet parent dans la relation. La table ou l’objet parent se trouve du côté « un » d’une relation un-à-plusieurs.

5. Faites glisser le nœud parent (ou les éléments individuels du nœud parent) de la fenêtre **sources de données** vers une cible de dépôt valide dans le concepteur.

     Visual Studio génère du code XAML qui crée des contrôles liés aux données pour chaque élément que vous faites glisser. Le code XAML ajoute également une nouvelle <xref:System.Windows.Data.CollectionViewSource> pour la table ou l’objet parent aux ressources de la cible de déplacement. Pour certaines sources de données, Visual Studio génère également du code pour charger les données dans la table ou l’objet parent. Pour plus d’informations, consultez [lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. Dans la fenêtre **sources de données** , recherchez la table enfant ou l’objet associé. Les tables enfants et les objets connexes apparaissent comme des nœuds développables au bas de la liste de données du nœud parent.

7. Faites glisser le nœud enfant (ou les éléments individuels du nœud enfant) de la fenêtre **sources de données** vers une cible de dépôt valide dans le concepteur.

     Visual Studio génère du code XAML qui crée des contrôles liés aux données pour chacun des éléments que vous faites glisser. Le code XAML ajoute également une nouvelle <xref:System.Windows.Data.CollectionViewSource> pour la table ou l’objet enfant aux ressources de la cible de déplacement. Ce nouveau <xref:System.Windows.Data.CollectionViewSource> est lié à la propriété de la table ou de l’objet parent que vous venez de faire glisser vers le concepteur. Pour certaines sources de données, Visual Studio génère également du code pour charger les données dans la table ou l’objet enfant.

     L’illustration suivante montre la table **Orders** associée de la table **Customers** dans un DataSet dans la fenêtre **sources de données** .

     ![Fenêtre Sources de données montrant des relations](../data-tools/media/datasources2.gif)

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Créer des tables de recherche dans des applications WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)
