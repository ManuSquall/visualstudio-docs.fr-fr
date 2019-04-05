---
title: Lier des objets
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
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dedfc71636983a9cbe634551a88eb3de45cb1d99
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950338"
---
# <a name="bind-objects-in-visual-studio"></a>Lier des objets dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Visual Studio fournit des outils de conception pour travailler avec des objets personnalisés comme source de données dans votre application. Lorsque vous souhaitez stocker des données à partir d’une base de données dans un objet que vous lier aux contrôles d’interface utilisateur, l’approche recommandée consiste à utiliser Entity Framework pour générer l’ou les classes. Entité Frameworkautogenerates tous le suivi des modifications code réutilisable, ce qui signifie que les modifications apportées aux objets locaux sont automatiquement rendues persistantes dans la base de données lorsque vous appelez AcceptChanges sur l’objet DbSet.    Pour plus d’informations, consultez [Documentation d’Entity Framework](https://ef.readthedocs.org/en/latest/).

> [!TIP]
>  Les approches de liaison de l’objet dans cet article uniquement convient si votre application est déjà basée sur des jeux de données. Ces approches peuvent également être utilisées si vous êtes déjà familiarisé avec les jeux de données et les données que vous allez traiter sont tabulaire et pas trop complexe ou trop important. Pour obtenir un exemple encore plus simple, impliquant le chargement des données directement dans des objets à l’aide d’un DataReader et de mise à jour manuelle de l’interface utilisateur sans liaison de données, consultez [créer une application de données simple à l’aide d’ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Exigences de l’objet
 La seule exigence pour les objets personnalisés travailler avec les données des outils de conception dans Visual Studio est que l’objet doit au moins une propriété publique.

 En règle générale, les objets personnalisés ne nécessitent pas tout des interfaces spécifiques, les constructeurs ou les attributs d’agir comme source de données pour une application. Toutefois, si vous souhaitez faire glisser l’objet à partir de la **des Sources de données** fenêtre à une aire de conception pour créer un contrôle lié aux données, et si l’objet implémente le <xref:System.ComponentModel.ITypedList> ou <xref:System.ComponentModel.IListSource> interface, l’objet doit avoir une valeur par défaut constructeur. Sinon, Visual Studio ne peut pas instancier l’objet de source de données, et une erreur s’affiche lorsque vous faites glisser l’élément vers l’aire de conception.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Exemples d’utilisation des objets personnalisés comme sources de données
 Bien qu’il existe des innombrables façons d’implémenter votre logique d’application lorsque vous travaillez avec des objets comme source de données, il les bases de données sont quelques opérations standards qui peuvent être simplifiées en utilisant les objets TableAdapter générés Visual Studio pour SQL. Cette page explique comment implémenter ces processus standards à l’aide de TableAdapters.It ne vise pas comme guide pour la création de vos objets personnalisés. Par exemple, vous allez généralement effectuer les opérations standards suivantes indépendamment de l’implémentation spécifique de vos objets, ou la logique de l’application :

-   Chargement des données dans des objets (généralement à partir d’une base de données).

-   Création d’une collection typée d’objets.

-   Ajout et suppression d’objets dans une collection.

-   Afficher les données d’objet aux utilisateurs sur un formulaire.

-   Modification des données dans un objet.

-   Enregistrer les données à partir d’objets dans la base de données.

> [!NOTE]
>  Afin de mieux comprendre et fournir le contexte pour les exemples de cette page, nous vous suggérons d’effectuer ce qui suit : [Procédure pas à pas : Connexion aux données dans des objets (Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05). Cette procédure pas à pas crée les objets présentés ici.

### <a name="loaddata-into-objects"></a>LoadData dans des objets
 Pour cet exemple, vous chargez des données dans vos objets à l’aide de TableAdapters. Par défaut, les TableAdapters sont créés avec deux types de méthodes qui extraire des données à partir d’une base de données et remplissent les tables de données.

- Le `TableAdapter.Fill` méthode remplit une table de données existante avec les données retournées.

- Le `TableAdapter.GetData` méthode retourne une nouvelle table de données remplie avec des données.

  Le moyen le plus simple pour charger vos objets personnalisés avec des données consiste à appeler le `TableAdapter.GetData` (méthode), boucler dans la collection de lignes dans la table de données retournée et remplir chaque objet avec les valeurs dans chaque ligne. Vous pouvez créer un `GetData` méthode qui retourne une table de données remplie pour toute requête ajoutée à un TableAdapter.

> [!NOTE]
>  Visual Studio nomme les requêtes TableAdapter `Fill` et `GetData` par défaut, mais ces noms peuvent être modifiés à n’importe quel nom de méthode valide.

 L’exemple suivant montre comment parcourir les lignes dans une table de données et remplir un objet avec les données :

 [!code-csharp[VbRaddataConnecting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs#4)]
 [!code-vb[VbRaddataConnecting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb#4)]

### <a name="create-a-typed-collection-of-objects"></a>Créer une collection typée d’objets
 Vous pouvez créer des classes de collection pour vos objets, ou utiliser les collections typées qui sont fournies automatiquement par le [composant BindingSource](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9).

 Lorsque vous créez une classe de collection personnalisée pour les objets, nous vous suggérons de que vous héritez de <xref:System.ComponentModel.BindingList%601>. Cette classe générique fournit des fonctionnalités pour administrer votre collection, ainsi que la possibilité de déclencher des événements qui envoient des notifications à l’infrastructure de liaison de données dans les Windows Forms.

 La collection générée automatiquement dans le <xref:System.Windows.Forms.BindingSource> utilise un <xref:System.ComponentModel.BindingList%601> pour sa collection typée. Si votre application ne nécessite pas de fonctionnalités supplémentaires, vous pouvez conserver votre collection dans le <xref:System.Windows.Forms.BindingSource>. Pour plus d’informations, consultez le <xref:System.Windows.Forms.BindingSource.List%2A> propriété de la <xref:System.Windows.Forms.BindingSource> classe.

> [!NOTE]
>  Si votre collection requiert des fonctionnalités non fournies par l’implémentation de base de la <xref:System.ComponentModel.BindingList%601>, vous devez créer une collection personnalisée, vous pouvez ajouter à la classe en fonction des besoins.

 Le code suivant montre comment créer la classe pour une collection fortement typée de `Order` objets :

 [!code-csharp[VbRaddataConnecting#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#8)]
 [!code-vb[VbRaddataConnecting#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#8)]

### <a name="addobjects-to-a-collection"></a>Addobjects à une collection
 Ajouter des objets à une collection en appelant le `Add` méthode de votre classe de collection personnalisée ou de la <xref:System.Windows.Forms.BindingSource>.

 Pour obtenir un exemple d’ajout d’une collection en utilisant un <xref:System.Windows.Forms.BindingSource>, consultez le `LoadCustomers` méthode dans [procédure pas à pas : Connexion aux données dans des objets (Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

 Pour obtenir un exemple d’ajout d’objets à une collection personnalisée, consultez le `LoadOrders` méthode dans [procédure pas à pas : Connexion aux données dans des objets (Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

> [!NOTE]
>  Le `Add` méthode est fournie automatiquement pour votre collection personnalisée lorsque vous héritez de <xref:System.ComponentModel.BindingList%601>.

 Le code suivant montre comment ajouter des objets à la collection typée dans un <xref:System.Windows.Forms.BindingSource>:

 [!code-csharp[VbRaddataConnecting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#5)]
 [!code-vb[VbRaddataConnecting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#5)]

 Le code suivant montre comment ajouter des objets à une collection typée qui hérite de <xref:System.ComponentModel.BindingList%601>:

> [!NOTE]
>  Dans cet exemple le `Orders` collection est une propriété de la `Customer` objet.

 [!code-csharp[VbRaddataConnecting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#6)]
 [!code-vb[VbRaddataConnecting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#6)]

### <a name="removeobjects-from-a-collection"></a>Supprimer des objets d’une collection
 Supprimer des objets d’une collection en appelant le `Remove` ou `RemoveAt` méthode de votre classe de collection personnalisée ou de <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
>  Le `Remove` et `RemoveAt` méthodes sont fournies automatiquement pour votre collection personnalisée lorsque vous héritez de <xref:System.ComponentModel.BindingList%601>.

 Le code suivant montre comment localiser et supprimer des objets de la collection typée dans un <xref:System.Windows.Forms.BindingSource> avec la <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> méthode :

 [!code-csharp[VbRaddataConnecting#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#7)]
 [!code-vb[VbRaddataConnecting#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#7)]

### <a name="displayobject-data-to-users"></a>Données DisplayObject aux utilisateurs
 Pour afficher les données dans des objets aux utilisateurs, créez une source de données objet à l’aide la **Configuration de Source de données** Assistant, puis faites glisser l’objet entier ou les propriétés individuelles sur votre formulaire à partir de la **des Sources de données**fenêtre.

### <a name="modify-the-data-in-objects"></a>Modifier les données dans des objets
 Pour modifier les données dans des objets personnalisés qui sont liés aux données aux contrôles Windows Forms, modifiez simplement les données dans le contrôle lié (ou directement dans les propriétés de l’objet). Architecture de liaison de données met à jour les données dans l’objet.

 Si votre application nécessite le suivi de modifications et la restauration de modifications proposées à leurs valeurs d’origine, vous devez implémenter cette fonctionnalité dans votre modèle objet. Pour obtenir des exemples de façon dont les tables de données de suivent les modifications proposées, consultez <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>, et <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="savedata-in-objects-back-to-the-database"></a>SaveData dans des objets dans la base de données
 Enregistrer les données dans la base de données en passant les valeurs à partir de votre objet pour les méthodes DBDirect du TableAdapter.

 Visual Studio crée des méthodes DBDirect qui peuvent être exécutées directement sur la base de données. Ces méthodes ne nécessitent pas d’objets DataSet ou DataTable.

|Méthode DBDirect du TableAdapter|Description|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Ajoute de nouveaux enregistrements à une base de données, ce qui vous permet de passer des valeurs de colonne individuelles comme paramètres de méthode.|
|`TableAdapter.Update`|Mises à jour les enregistrements dans une base de données existants. La méthode de mise à jour prend les valeurs d’origine et de la nouvelle colonne en tant que paramètres de méthode. Les valeurs d’origine sont utilisées pour rechercher l’enregistrement d’origine et les nouvelles valeurs sont utilisées pour mettre à jour cet enregistrement.<br /><br /> Le `TableAdapter.Update` méthode est également utilisée pour rapprocher les modifications dans un jeu de données à la base de données, en prenant un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, ou un tableau de <xref:System.Data.DataRow>s en tant que paramètres de méthode.|
|`TableAdapter.Delete`|Supprime les enregistrements existants de la base de données en fonction des valeurs de colonne d’origine passés en tant que paramètres de méthode.|

 Pour enregistrer des données à partir d’une collection d’objets, parcourez la collection d’objets (par exemple, à l’aide d’une boucle for next). Envoyez les valeurs pour chaque objet à la base de données à l’aide des méthodes DBDirect du TableAdapter.

 L’exemple suivant montre comment utiliser le `TableAdapter.Insert` méthode DBDirect pour ajouter un nouveau client directement dans la base de données :

 [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
 [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

## <a name="see-also"></a>Voir aussi
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
