---
title: Objets personnalisés de liaison de données
description: Liez des objets en tant que sources de données dans Visual Studio. Utilisez les outils au moment du design pour travailler avec des objets personnalisés comme source de données dans votre application.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ad8b5f502953912e2de7383afa4a86ff749c5724
ms.sourcegitcommit: 63ff7cb85b3baeeb713240d17bb2a18497f3741d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94518592"
---
# <a name="bind-objects-as-data-sources-in-visual-studio"></a>Lier des objets en tant que sources de données dans Visual Studio

Visual Studio fournit des outils au moment du design pour travailler avec des objets personnalisés comme source de données dans votre application. Lorsque vous souhaitez stocker des données à partir d’une base de données dans un objet que vous liez à des contrôles d’interface utilisateur, l’approche recommandée consiste à utiliser Entity Framework pour générer la classe ou les classes. Entity Framework génère automatiquement l’ensemble du code de suivi des modifications, ce qui signifie que toutes les modifications apportées aux objets locaux sont automatiquement rendues persistantes dans la base de données lorsque vous appelez AcceptChanges sur l’objet DbSet. Pour plus d’informations, consultez [la Documentation Entity Framework](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Les approches de liaison d’objets de cet article ne doivent être prises en compte que si votre application est déjà basée sur des jeux de données. Vous pouvez également utiliser ces approches si vous êtes déjà familiarisé avec les jeux de données et que les données que vous allez traiter sont tabulaires et non trop complexes ou trop volumineuses. Pour un exemple encore plus simple, impliquant le chargement de données directement dans des objets à l’aide d’un DataReader et la mise à jour manuelle de l’interface utilisateur sans liaison de données, consultez [créer une application de données simple à l’aide de ADO.net](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Exigences relatives aux objets

La seule exigence pour que les objets personnalisés fonctionnent avec les outils de conception de données dans Visual Studio est que l’objet a besoin d’au moins une propriété publique.

En règle générale, les objets personnalisés ne nécessitent pas d’interfaces, de constructeurs ou d’attributs spécifiques pour agir en tant que source de données pour une application. Toutefois, si vous souhaitez faire glisser l’objet de la fenêtre **sources de données** vers une aire de conception pour créer un contrôle lié aux données, et si l’objet implémente l' <xref:System.ComponentModel.ITypedList> interface ou <xref:System.ComponentModel.IListSource> , l’objet doit avoir un constructeur par défaut. Dans le cas contraire, Visual Studio ne peut pas instancier l’objet source de données et affiche une erreur quand vous faites glisser l’élément sur l’aire de conception.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Exemples d’utilisation d’objets personnalisés comme sources de données

Bien qu’il existe des moyens innombrables d’implémenter votre logique d’application lorsque vous travaillez avec des objets comme source de données, pour les bases de données SQL, il existe quelques opérations standard qui peuvent être simplifiées à l’aide des objets TableAdapter générés par Visual Studio. Cette page explique comment implémenter ces processus standard à l’aide de TableAdapters. Il n’est pas conçu comme un guide pour la création de vos objets personnalisés. Par exemple, vous effectuerez généralement les opérations standard suivantes, quelle que soit l’implémentation spécifique de vos objets, ou la logique de l’application :

- Chargement de données dans des objets (en général à partir d’une base de données).

- Création d’une collection typée d’objets.

- Ajout et suppression d’objets dans une collection.

- Affichage des données de l’objet pour les utilisateurs d’un formulaire.

- Modification/modification des données dans un objet.

- Enregistrement des données des objets dans la base de données.

### <a name="load-data-into-objects"></a>Charger des données dans des objets

Pour cet exemple, vous chargez des données dans vos objets à l’aide de TableAdapters. Par défaut, les TableAdapters sont créés avec deux genres de méthodes qui extraient des données d’une base de données et renseignent les tables de données.

- La `TableAdapter.Fill` méthode remplit une table de données existante avec les données retournées.

- La `TableAdapter.GetData` méthode retourne une nouvelle table de données remplie avec des données.

Le moyen le plus simple de charger vos objets personnalisés avec des données consiste à appeler la `TableAdapter.GetData` méthode, à parcourir la collection de lignes dans la table de données retournée et à remplir chaque objet avec les valeurs de chaque ligne. Vous pouvez créer une `GetData` méthode qui retourne une table de données remplie pour toute requête ajoutée à un TableAdapter.

> [!NOTE]
> Visual Studio nomme les requêtes TableAdapter `Fill` et `GetData` par défaut, mais vous pouvez remplacer ces noms par n’importe quel nom de méthode valide.

L’exemple suivant montre comment effectuer une boucle dans les lignes d’une table de données et comment remplir un objet avec des données :

[!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
[!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]

### <a name="create-a-typed-collection-of-objects"></a>Créer une collection typée d’objets

Vous pouvez créer des classes de collection pour vos objets, ou utiliser les collections typées qui sont fournies automatiquement par le [composant BindingSource](/dotnet/framework/winforms/controls/bindingsource-component).

Lorsque vous créez une classe de collection personnalisée pour des objets, nous vous suggérons d’hériter de <xref:System.ComponentModel.BindingList%601> . Cette classe générique fournit des fonctionnalités pour administrer votre collection, ainsi que la possibilité de déclencher des événements qui envoient des notifications à l’infrastructure de liaison de données dans Windows Forms.

La collection générée automatiquement dans le <xref:System.Windows.Forms.BindingSource> utilise un <xref:System.ComponentModel.BindingList%601> pour sa collection typée. Si votre application ne nécessite pas de fonctionnalités supplémentaires, vous pouvez gérer votre collection dans le <xref:System.Windows.Forms.BindingSource> . Pour plus d’informations, consultez la <xref:System.Windows.Forms.BindingSource.List%2A> propriété de la <xref:System.Windows.Forms.BindingSource> classe.

> [!NOTE]
> Si votre collection requiert des fonctionnalités qui ne sont pas fournies par l’implémentation de base de <xref:System.ComponentModel.BindingList%601> , vous devez créer une collection personnalisée afin de pouvoir l’ajouter à la classe en fonction des besoins.

Le code suivant montre comment créer la classe pour une collection fortement typée d' `Order` objets :

[!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
[!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]

### <a name="add-objects-to-a-collection"></a>Ajouter des objets à une collection

Vous ajoutez des objets à une collection en appelant la `Add` méthode de votre classe de collection personnalisée ou de <xref:System.Windows.Forms.BindingSource> .

> [!NOTE]
> La `Add` méthode est fournie automatiquement pour votre collection personnalisée lorsque vous héritez de <xref:System.ComponentModel.BindingList%601> .

Le code suivant montre comment ajouter des objets à la collection typée dans <xref:System.Windows.Forms.BindingSource> :

[!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
[!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]

Le code suivant montre comment ajouter des objets à une collection typée qui hérite de <xref:System.ComponentModel.BindingList%601> :

> [!NOTE]
> Dans cet exemple, la `Orders` collection est une propriété de l' `Customer` objet.

[!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
[!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]

### <a name="remove-objects-from-a-collection"></a>Supprimer des objets d’une collection

Pour supprimer des objets d’une collection, appelez `Remove` la `RemoveAt` méthode ou de votre classe de collection personnalisée ou de <xref:System.Windows.Forms.BindingSource> .

> [!NOTE]
> Les `Remove` `RemoveAt` méthodes et sont fournies automatiquement pour votre collection personnalisée lorsque vous héritez de <xref:System.ComponentModel.BindingList%601> .

Le code suivant montre comment localiser et supprimer des objets de la collection typée dans un <xref:System.Windows.Forms.BindingSource> avec la <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> méthode :

[!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
[!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]

### <a name="display-object-data-to-users"></a>Afficher les données d’objet aux utilisateurs

Pour afficher les données des objets pour les utilisateurs, créez une source de données d’objet à l’aide de l’Assistant **configuration de source de données** , puis faites glisser l’objet entier ou les propriétés individuelles sur votre formulaire à partir de la fenêtre sources de **données** .

### <a name="modify-the-data-in-objects"></a>Modifier les données dans les objets

Pour modifier des données dans des objets personnalisés qui sont liés aux données de Windows Forms contrôles, modifiez simplement les données du contrôle lié (ou directement dans les propriétés de l’objet). L’architecture de liaison de données met à jour les données dans l’objet.

Si votre application requiert le suivi des modifications et la restauration des modifications proposées à leurs valeurs d’origine, vous devez implémenter cette fonctionnalité dans votre modèle objet. Pour obtenir des exemples de la façon dont les tables de données effectuent le suivi des modifications proposées, consultez <xref:System.Data.DataRowState> , <xref:System.Data.DataSet.HasChanges%2A> et <xref:System.Data.DataTable.GetChanges%2A> .

### <a name="save-data-in-objects-back-to-the-database"></a>Réenregistrer les données dans les objets dans la base de données

Réenregistrez les données dans la base de données en passant les valeurs de votre objet aux méthodes DBDirect du TableAdapter.

Visual Studio crée des méthodes DBDirect qui peuvent être exécutées directement sur la base de données. Ces méthodes ne nécessitent pas d’objets DataSet ou DataTable.

|Méthode DBDirect du TableAdapter|Description|
| - |-----------------|
|`TableAdapter.Insert`|Ajoute de nouveaux enregistrements à une base de données, ce qui vous permet de transmettre des valeurs de colonne individuelles en tant que paramètres de méthode.|
|`TableAdapter.Update`|Met à jour les enregistrements existants dans une base de données. La méthode Update prend des valeurs de colonne originales et nouvelles comme paramètres de méthode. Les valeurs d’origine sont utilisées pour localiser l’enregistrement d’origine, et les nouvelles valeurs sont utilisées pour mettre à jour cet enregistrement.<br /><br /> La `TableAdapter.Update` méthode est également utilisée pour réconcilier les modifications apportées à un DataSet dans la base de données, en acceptant un <xref:System.Data.DataSet> tableau,, <xref:System.Data.DataTable> <xref:System.Data.DataRow> ou <xref:System.Data.DataRow> en tant que paramètres de méthode.|
|`TableAdapter.Delete`|Supprime les enregistrements existants de la base de données en fonction des valeurs de colonne d’origine passées en tant que paramètres de méthode.|

Pour enregistrer des données à partir d’une collection d’objets, parcourez la collection d’objets (par exemple, à l’aide d’une boucle for-Next). Envoyez les valeurs de chaque objet à la base de données à l’aide des méthodes DBDirect du TableAdapter.

L’exemple suivant montre comment utiliser la `TableAdapter.Insert` méthode DBDirect pour ajouter un nouveau client directement dans la base de données :

[!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
[!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
