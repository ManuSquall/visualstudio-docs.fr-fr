---
title: Créer des tables de recherche dans des applications WPF | Microsoft Docs
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
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6816b7465b8a3271ec6ebc0db5046d76e60ec5b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657423"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Créer des tables de recherche dans des applications WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La *table de recherche* de terme (parfois appelée « *liaison de recherche*») décrit un contrôle qui affiche des informations à partir d’une table de données en fonction de la valeur d’un champ de clé étrangère dans une autre table. Vous pouvez créer une table de recherche en faisant glisser le nœud principal d’une table ou d’un objet parent dans la fenêtre **sources de données** vers un contrôle qui est déjà lié à une colonne ou une propriété dans une table enfant associée.

 Prenons l’exemple d’une table de `Orders` dans une base de données Sales. Chaque enregistrement de la table `Orders` comprend un `CustomerID` qui indique le client qui a passé la commande. La `CustomerID` est une clé étrangère qui pointe vers un enregistrement de client dans la table `Customers`. Lorsque vous affichez une liste de commandes à partir de la table `Orders`, vous pouvez afficher le nom du client réel au lieu du `CustomerID`. Étant donné que le nom du client figure dans la table `Customers`, vous devez créer une table de recherche pour afficher le nom du client. La table de recherche utilise la valeur `CustomerID` dans l’enregistrement `Orders` pour naviguer dans la relation et retourner le nom du client.

## <a name="to-create-a-lookup-table"></a>Pour créer une table de choix

1. Ajoutez l’un des types suivants de sources de données avec les données associées à votre projet :

    - Jeu de données ou Entity Data Model.

    - Service de données WCF, service WCF ou service Web. Pour plus d’informations, consultez [Comment : se connecter à des données dans un service](../data-tools/how-to-connect-to-data-in-a-service.md).

    - Objets. Pour plus d’informations, consultez [Comment : se connecter à des données dans des objets](https://msdn.microsoft.com/library/862fd351-0f4d-4220-9743-6103b87dc24b).

    > [!NOTE]
    > Avant de pouvoir créer une table de correspondance, deux tables ou objets associés doivent exister comme source de données pour le projet.

2. Ouvrez le**Concepteur WPF**et assurez-vous que le concepteur contient un conteneur qui est une cible de dépôt valide pour les éléments de la fenêtre **sources de données** .

     Pour plus d’informations sur les cibles de dépôt valides, consultez [lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

3. Dans le menu **Données**, cliquez sur **Afficher les sources de données** pour ouvrir la fenêtre **Sources de données**.

4. Développez les nœuds dans la fenêtre **sources de données** , jusqu’à ce que vous puissiez voir la table ou l’objet parent et la table enfant ou l’objet associé.

    > [!NOTE]
    > La table enfant ou l’objet associé est le nœud qui apparaît en tant que nœud enfant pouvant être développé sous la table ou l’objet parent.

5. Cliquez sur le menu déroulant du nœud enfant, puis sélectionnez **Détails**.

6. Développez le nœud enfant.

7. Sous le nœud enfant, cliquez sur le menu déroulant de l’élément qui met en relation les données enfants et parentes. (Dans l’exemple précédent, il s’agit du nœud **CustomerID** .) Sélectionnez l’un des types de contrôles suivants qui prennent en charge la liaison de recherche :

    - **ComboBox**

    - **ListBox**

    - **ListView**

        > [!NOTE]
        > Si le contrôle **ListBox** ou **ListView** n’apparaît pas dans la liste, vous pouvez ajouter ces contrôles à la liste. Pour plus d’informations, consultez [définir le contrôle à créer lors d’une opération de glisser-déplacer à partir de la fenêtre sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    - Tout contrôle personnalisé qui dérive de <xref:System.Windows.Controls.Primitives.Selector>.

        > [!NOTE]
        > Pour plus d’informations sur la façon d’ajouter des contrôles personnalisés à la liste de contrôles que vous pouvez sélectionner pour les éléments dans la fenêtre **sources de données** , consultez [Ajouter des contrôles personnalisés à la fenêtre sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).

8. Faites glisser le nœud enfant de la fenêtre **sources de données** vers un conteneur dans le Concepteur WPF. (Dans l’exemple précédent, le nœud enfant est le nœud **Orders** .)

     Visual Studio génère du code XAML qui crée des contrôles liés aux données pour chaque élément que vous faites glisser. Le code XAML ajoute également une nouvelle <xref:System.Windows.Data.CollectionViewSource> pour la table ou l’objet enfant aux ressources de la cible de déplacement. Pour certaines sources de données, Visual Studio génère également du code pour charger des données dans la table ou l’objet. Pour plus d’informations, consultez [lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

9. Faites glisser le nœud parent de la fenêtre **sources de données** vers le contrôle de liaison de recherche que vous avez créé précédemment. (Dans l’exemple précédent, le nœud parent est le nœud **Customers** ).

     Visual Studio définit des propriétés sur le contrôle pour configurer la liaison de recherche. Le tableau suivant répertorie les propriétés que Visual Studio modifie. Si nécessaire, vous pouvez modifier ces propriétés dans le XAML ou dans la fenêtre **Propriétés** .

    |Property|Explication du paramètre|
    |--------------|----------------------------|
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Cette propriété spécifie la collection ou la liaison utilisée pour récupérer les données affichées dans le contrôle. Visual Studio affecte à cette propriété la <xref:System.Windows.Data.CollectionViewSource> pour les données parentes que vous avez déplacées vers le contrôle.|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Cette propriété spécifie le chemin d’accès de l’élément de données affiché dans le contrôle. Visual Studio définit cette propriété sur la première colonne ou propriété dans les données parentes, après la clé primaire, qui a un type de données String.<br /><br /> Si vous souhaitez afficher une colonne ou une propriété différente dans les données parentes, remplacez cette propriété par le chemin d’accès d’une autre propriété.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio lie cette propriété à la colonne ou à la propriété des données enfants que vous avez déplacées vers le concepteur. Il s’agit de la clé étrangère vers les données parentes.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio définit cette propriété sur le chemin d’accès de la colonne ou de la propriété des données enfants qui est la clé étrangère aux données parentes.|

## <a name="see-also"></a>Voir aussi
 [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [afficher des données connexes dans des applications WPF](../data-tools/display-related-data-in-wpf-applications.md) [procédure pas à pas : affichage de données connexes dans une application WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
