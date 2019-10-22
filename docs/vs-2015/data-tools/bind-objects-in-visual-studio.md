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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c487df5623a233146655593265e15c34a884de3c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672994"
---
# <a name="bind-objects-in-visual-studio"></a>Lier des objets dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio fournit des outils au moment du design pour travailler avec des objets personnalisés comme source de données dans votre application. Lorsque vous souhaitez stocker des données à partir d’une base de données dans un objet que vous liez à des contrôles d’interface utilisateur, l’approche recommandée consiste à utiliser Entity Framework pour générer la classe ou les classes. Entity Frameworkautogenerates tout le code de suivi des modifications, ce qui signifie que toutes les modifications apportées aux objets locaux sont automatiquement rendues persistantes dans la base de données lorsque vous appelez AcceptChanges sur l’objet DbSet.    Pour plus d’informations, consultez [la Documentation Entity Framework](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Les approches de liaison d’objets de cet article ne doivent être prises en compte que si votre application est déjà basée sur des jeux de données. Ces approches peuvent également être utilisées si vous êtes déjà familiarisé avec les jeux de données, et les données que vous allez traiter sont tabulaires et non trop complexes ou trop volumineuses. Pour un exemple encore plus simple, impliquant le chargement de données directement dans des objets à l’aide d’un DataReader et la mise à jour manuelle de l’interface utilisateur sans liaison de données, consultez [créer une application de données simple à l’aide de ADO.net](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Exigences relatives aux objets
 La seule exigence pour que les objets personnalisés fonctionnent avec les outils de conception de données dans Visual Studio est que l’objet a besoin d’au moins une propriété publique.

 En règle générale, les objets personnalisés ne nécessitent pas d’interfaces, de constructeurs ou d’attributs spécifiques pour agir en tant que source de données pour une application. Toutefois, si vous souhaitez faire glisser l’objet de la fenêtre **sources de données** vers une aire de conception pour créer un contrôle lié aux données, et si l’objet implémente l’interface <xref:System.ComponentModel.ITypedList> ou <xref:System.ComponentModel.IListSource>, l’objet doit avoir un constructeur par défaut. Dans le cas contraire, Visual Studio ne peut pas instancier l’objet source de données et affiche une erreur quand vous faites glisser l’élément sur l’aire de conception.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Exemples d’utilisation d’objets personnalisés comme sources de données
 Bien qu’il existe des moyens innombrables d’implémenter votre logique d’application lorsque vous travaillez avec des objets comme source de données, pour les bases de données SQL, il existe quelques opérations standard qui peuvent être simplifiées à l’aide des objets TableAdapter générés par Visual Studio. Cette page explique comment implémenter ces processus standard à l’aide de TableAdapters.It n’est pas conçu comme un guide pour la création de vos objets personnalisés. Par exemple, vous effectuerez généralement les opérations standard suivantes, quelle que soit l’implémentation spécifique de vos objets, ou la logique de l’application :

- Chargement de données dans des objets (en général à partir d’une base de données).

- Création d’une collection typée d’objets.

- Ajout et suppression d’objets dans une collection.

- Affichage des données de l’objet pour les utilisateurs d’un formulaire.

- Modification/modification des données dans un objet.

- Enregistrement des données des objets dans la base de données.

> [!NOTE]
> Pour mieux comprendre et fournir un contexte pour les exemples de cette page, nous vous suggérons d’effectuer les opérations suivantes : [procédure pas à pas : connexion à des données dans des objets (Windows Forms)](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05). Cette procédure pas à pas crée les objets décrits ici.

### <a name="loaddata-into-objects"></a>LoadData en objets
 Pour cet exemple, vous chargez des données dans vos objets à l’aide de TableAdapters. Par défaut, les TableAdapters sont créés avec deux genres de méthodes qui extraient des données d’une base de données et renseignent les tables de données.

- La méthode `TableAdapter.Fill` remplit une table de données existante avec les données retournées.

- La méthode `TableAdapter.GetData` retourne une nouvelle table de données remplie avec des données.

  Le moyen le plus simple de charger vos objets personnalisés avec des données consiste à appeler la méthode `TableAdapter.GetData`, à parcourir la collection de lignes dans la table de données retournée et à remplir chaque objet avec les valeurs de chaque ligne. Vous pouvez créer une méthode `GetData` qui retourne une table de données remplie pour toute requête ajoutée à un TableAdapter.

> [!NOTE]
> Visual Studio nomme les requêtes TableAdapter `Fill` et `GetData` par défaut, mais ces noms peuvent être remplacés par n’importe quel nom de méthode valide.

 L’exemple suivant montre comment effectuer une boucle dans les lignes d’une table de données et comment remplir un objet avec des données :

 [!code-csharp[VbRaddataConnecting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs#4)]
 [!code-vb[VbRaddataConnecting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb#4)]

### <a name="create-a-typed-collection-of-objects"></a>Créer une collection typée d’objets
 Vous pouvez créer des classes de collection pour vos objets, ou utiliser les collections typées qui sont fournies automatiquement par le [composant BindingSource](https://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9).

 Lorsque vous créez une classe de collection personnalisée pour des objets, nous vous suggérons d’hériter de <xref:System.ComponentModel.BindingList%601>. Cette classe générique fournit des fonctionnalités pour administrer votre collection, ainsi que la possibilité de déclencher des événements qui envoient des notifications à l’infrastructure de liaison de données dans Windows Forms.

 La collection générée automatiquement dans le <xref:System.Windows.Forms.BindingSource> utilise une <xref:System.ComponentModel.BindingList%601> pour sa collection typée. Si votre application ne nécessite pas de fonctionnalités supplémentaires, vous pouvez gérer votre collection dans le <xref:System.Windows.Forms.BindingSource>. Pour plus d’informations, consultez la propriété <xref:System.Windows.Forms.BindingSource.List%2A> de la classe <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> Si votre collection requiert des fonctionnalités qui ne sont pas fournies par l’implémentation de base du <xref:System.ComponentModel.BindingList%601>, vous devez créer une collection personnalisée afin de pouvoir l’ajouter à la classe si nécessaire.

 Le code suivant montre comment créer la classe pour une collection fortement typée d’objets `Order` :

 [!code-csharp[VbRaddataConnecting#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#8)]
 [!code-vb[VbRaddataConnecting#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#8)]

### <a name="addobjects-to-a-collection"></a>AddObjects à une collection
 Vous ajoutez des objets à une collection en appelant la méthode `Add` de votre classe de collection personnalisée ou de la <xref:System.Windows.Forms.BindingSource>.

 Pour obtenir un exemple d’ajout à une collection à l’aide d’un <xref:System.Windows.Forms.BindingSource>, consultez la méthode `LoadCustomers` dans [procédure pas à pas : connexion à des données dans des objets (Windows Forms)](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

 Pour obtenir un exemple d’ajout d’objets à une collection personnalisée, consultez la méthode `LoadOrders` dans [procédure pas à pas : connexion à des données dans des objets (Windows Forms)](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

> [!NOTE]
> La méthode `Add` est fournie automatiquement pour votre collection personnalisée lorsque vous héritez de <xref:System.ComponentModel.BindingList%601>.

 Le code suivant montre comment ajouter des objets à la collection typée dans une <xref:System.Windows.Forms.BindingSource> :

 [!code-csharp[VbRaddataConnecting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#5)]
 [!code-vb[VbRaddataConnecting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#5)]

 Le code suivant montre comment ajouter des objets à une collection typée qui hérite de <xref:System.ComponentModel.BindingList%601> :

> [!NOTE]
> Dans cet exemple, la collection `Orders` est une propriété de l’objet `Customer`.

 [!code-csharp[VbRaddataConnecting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#6)]
 [!code-vb[VbRaddataConnecting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#6)]

### <a name="removeobjects-from-a-collection"></a>Removeobjects à partir d’une collection
 Pour supprimer des objets d’une collection, appelez la méthode `Remove` ou `RemoveAt` de votre classe de collection personnalisée ou de <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> Les méthodes `Remove` et `RemoveAt` sont fournies automatiquement pour votre collection personnalisée lorsque vous héritez de <xref:System.ComponentModel.BindingList%601>.

 Le code suivant montre comment localiser et supprimer des objets de la collection typée dans une <xref:System.Windows.Forms.BindingSource> avec la méthode <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> :

 [!code-csharp[VbRaddataConnecting#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#7)]
 [!code-vb[VbRaddataConnecting#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#7)]

### <a name="displayobject-data-to-users"></a>Données DisplayObject pour les utilisateurs
 Pour afficher les données des objets pour les utilisateurs, créez une source de données d’objet à l’aide de l’Assistant **configuration de source de données** , puis faites glisser l’objet entier ou les propriétés individuelles sur votre formulaire à partir de la fenêtre sources de **données** .

### <a name="modify-the-data-in-objects"></a>Modifier les données dans les objets
 Pour modifier des données dans des objets personnalisés qui sont liés aux données de Windows Forms contrôles, modifiez simplement les données du contrôle lié (ou directement dans les propriétés de l’objet). L’architecture de liaison de données met à jour les données dans l’objet.

 Si votre application requiert le suivi des modifications et la restauration des modifications proposées à leurs valeurs d’origine, vous devez implémenter cette fonctionnalité dans votre modèle objet. Pour obtenir des exemples de la façon dont les tables de données effectuent le suivi des modifications proposées, consultez <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A> et <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="savedata-in-objects-back-to-the-database"></a>SaveData dans les objets dans la base de données
 Réenregistrez les données dans la base de données en passant les valeurs de votre objet aux méthodes DBDirect du TableAdapter.

 Visual Studio crée des méthodes DBDirect qui peuvent être exécutées directement sur la base de données. Ces méthodes ne nécessitent pas d’objets DataSet ou DataTable.

|Méthode DBDirect du TableAdapter|Description|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Ajoute de nouveaux enregistrements à une base de données, ce qui vous permet de transmettre des valeurs de colonne individuelles en tant que paramètres de méthode.|
|`TableAdapter.Update`|Met à jour les enregistrements existants dans une base de données. La méthode Update prend des valeurs de colonne originales et nouvelles comme paramètres de méthode. Les valeurs d’origine sont utilisées pour localiser l’enregistrement d’origine, et les nouvelles valeurs sont utilisées pour mettre à jour cet enregistrement.<br /><br /> La méthode `TableAdapter.Update` est également utilisée pour réconcilier les modifications apportées à un DataSet dans la base de données, en acceptant un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> ou un tableau de <xref:System.Data.DataRow>s comme paramètres de méthode.|
|`TableAdapter.Delete`|Supprime les enregistrements existants de la base de données en fonction des valeurs de colonne d’origine passées en tant que paramètres de méthode.|

 Pour enregistrer des données à partir d’une collection d’objets, parcourez la collection d’objets (par exemple, à l’aide d’une boucle for-Next). Envoyez les valeurs de chaque objet à la base de données à l’aide des méthodes DBDirect du TableAdapter.

 L’exemple suivant montre comment utiliser la méthode `TableAdapter.Insert` DBDirect pour ajouter un nouveau client directement dans la base de données :

 [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
 [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

## <a name="see-also"></a>Voir aussi
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
