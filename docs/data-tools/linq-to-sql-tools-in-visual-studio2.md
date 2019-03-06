---
title: Vue d’ensemble du Concepteur O/R
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4105a93d4ad459c8bc1cb3a7a20b37c69f311c12
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931635"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Outils LINQ to SQL dans Visual Studio

LINQ to SQL a été la première technologie de mapping objet-relationnel publiée par Microsoft. Il fonctionne bien dans les scénarios de base et continue à être pris en charge dans Visual Studio, mais il n’est plus en cours de développement. Utiliser LINQ to SQL lors de la mise à jour une application héritée qui utilise déjà, ou dans des applications simples qui utilisent SQL Server et ne nécessitent pas de mappage de plusieurs table. En règle générale, les nouvelles applications doivent utiliser Entity Framework lorsqu’une couche de Mappeur objet-relationnel est requise.

Dans Visual Studio, vous créez LINQ to SQL des classes qui représentent des tables SQL à l’aide de la **concepteur objet/relationnel** (**Concepteur O/R**).

Le **Concepteur O/R** a deux zones distinctes sur son aire de conception : le volet d’entités sur la gauche et le volet de méthodes sur la droite. Le volet d'entités est l'aire de conception principale qui affiche les classes d'entité, associations et hiérarchies d'héritage. Le volet de méthodes est l’aire de conception qui affiche les méthodes <xref:System.Data.Linq.DataContext> mappées aux procédures stockées et aux fonctions.

Le **Concepteur O/R** fournit une aire de conception visuelle pour la création de [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) classes d’entité et les associations (relations) qui sont basées sur des objets dans une base de données. En d’autres termes, le **Concepteur O/R** crée un modèle d’objet dans une application qui est mappé à des objets dans une base de données. Il génère également un fortement typée <xref:System.Data.Linq.DataContext> qui envoie et reçoit des données entre les classes d’entité et de la base de données. Le **Concepteur O/R** également fournit des fonctionnalités permettant de mapper des procédures stockées et des fonctions aux <xref:System.Data.Linq.DataContext> méthodes afin de retourner des données et remplir des classes d’entité. Enfin, le **Concepteur O/R** offre la possibilité de conception les relations d’héritage entre classes d’entité.

## <a name="open-the-or-designer"></a>Ouvrez le Concepteur O/R

Pour ajouter un LINQ à SQL entity model à votre projet, choisissez **projet** > **ajouter un nouvel élément**, puis sélectionnez **Classes LINQ to SQL** dans la liste des éléments de projet :

![Classes LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio crée un *.dbml* de fichier et l’ajoute à votre solution. C’est le fichier de mappage XML et ses fichiers de code connexes.

![Classes LINQ to SQL dans l’Explorateur de solutions](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

Lorsque vous sélectionnez le *.dbml* de fichiers, Visual Studio affiche la **Concepteur O/R** surface qui vous permet de créer visuellement le modèle. L’illustration suivante montre le concepteur après Northwind `Customers` et `Orders` tables ont été déplacés de **Explorateur de serveurs**. Notez la relation entre les tables.

![Concepteur LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> Le **Concepteur O/R** est un mappeur relationnel objet simple, car il prend en charge uniquement les relations de mappage 1:1. En d'autres termes, une classe d'entité peut uniquement avoir une relation de mappage 1:1 avec une table ou une vue de base de données. Le mappage complexe, tel que le mappage d’une classe d’entité à une table jointe, n’est pas pris en charge ; utiliser Entity Framework pour le mappage complex. En outre, le concepteur est un générateur de code unidirectionnel. Cela signifie que seules les modifications apportées à l'aire du concepteur sont répercutées dans le fichier de code. Les modifications manuelles au fichier de code ne sont pas répercutées dans le **Concepteur O/R**. Les modifications apportées manuellement dans le fichier de code sont remplacées lorsque le concepteur est enregistré et le code régénéré. Pour plus d’informations sur la façon d’ajouter le code utilisateur et d’étendre les classes générées par le **Concepteur O/R**, consultez [Comment : étendre le code généré par le Concepteur O/R](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>Créer et configurer le DataContext

Après avoir ajouté un **Classes LINQ to SQL** élément à un projet et ouvert le **Concepteur O/R**, l’aire de conception vide représente vide <xref:System.Data.Linq.DataContext> prêt à être configuré. Le <xref:System.Data.Linq.DataContext> est configuré avec les informations de connexion fournies par le premier élément glissé sur l’aire de conception. Par conséquent, <xref:System.Data.Linq.DataContext> est configuré en utilisant les informations de connexion du premier élément déposé sur l’aire de conception. Pour plus d’informations sur la <xref:System.Data.Linq.DataContext> , consultez classe [DataContext, méthodes (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Créer des classes d’entité qui mappent aux tables de base de données et des vues

Vous pouvez créer des classes d’entité mappées aux tables et vues en faisant glisser des tables de base de données et les vues de **Explorateur de serveurs** ou **Database Explorer** sur le **Concepteur O/R**. Comme indiqué dans la section précédente, <xref:System.Data.Linq.DataContext> est configuré avec les informations de connexion fournies par le premier élément glissé sur l’aire de conception. Si un élément suivant qui utilise une connexion différente est ajouté à la **Concepteur O/R**, vous pouvez modifier la connexion pour le <xref:System.Data.Linq.DataContext>. Pour plus d’informations, consultez [Comment : créer des classes LINQ to SQL mappées aux tables et vues (Concepteur O/R)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Créer des méthodes DataContext qui appellent des procédures stockées et fonctions

Vous pouvez créer <xref:System.Data.Linq.DataContext> méthodes qui appellent (sont mappées à) des procédures stockées et fonctions en les faisant glisser à partir de **Explorateur de serveurs** ou **Database Explorer** sur la **Concepteur O/R** . Procédures stockées et fonctions sont ajoutées à la **Concepteur O/R** en tant que méthodes de le <xref:System.Data.Linq.DataContext>.

> [!NOTE]
> Lorsque vous faites glisser des procédures stockées et des fonctions de **Explorateur de serveurs** ou **Database Explorer** sur le **Concepteur O/R**, le type de retour de généré <xref:System.Data.Linq.DataContext> méthode diffère selon l’endroit où vous placez l’élément. Pour plus d’informations, consultez [DataContext, méthodes (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configurer un DataContext pour utiliser des procédures stockées pour enregistrer les données entre les classes d’entité et une base de données

Comme mentionné précédemment, vous pouvez créer des méthodes <xref:System.Data.Linq.DataContext> qui appellent des procédures stockées et des fonctions. En outre, vous pouvez également affecter des procédures stockées qui sont utilisées pour la valeur par défaut LINQ au comportement d’exécution SQL, qui effectue des insertions, mises à jour et supprime. Pour plus d’informations, consultez [Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Héritage et Concepteur O/R

Comme d’autres objets, les classes LINQ to SQL peut utiliser l’héritage et être dérivée d’autres classes. Dans une base de données, les relations d'héritage sont créées de plusieurs façons. Le **Concepteur O/R** prend en charge le concept d’héritage à table unique tel qu’il est souvent implémenté dans les systèmes relationnels. Pour plus d’informations, consultez [Comment : configurer l’héritage à l’aide du Concepteur O/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Requêtes LINQ to SQL

Les classes d’entité créées par le **Concepteur O/R** sont conçus pour une utilisation avec [Language-Integrated query (LINQ)](/dotnet/csharp/linq/). Pour plus d’informations, consultez [Comment : demander des informations](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Séparer le code de classe DataContext et d’entité généré dans différents espaces de noms

Le **Concepteur O/R** fournit le **contexte Namespace** et **Entity Namespace** propriétés sur le <xref:System.Data.Linq.DataContext>. Ces propriétés déterminent dans quel espace de noms le <xref:System.Data.Linq.DataContext> et le code de classe entité est généré. Par défaut, ces propriétés sont vides, les <xref:System.Data.Linq.DataContext> et les classes d'entité étant générés dans l'espace de noms de l'application. Pour générer le code dans un espace de noms autre que l’espace de noms de l’application, entrez une valeur dans les propriétés **Espace de noms du contexte** et/ou **Espace de noms de l’entité**.

## <a name="reference-content"></a>Contenu de référence

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Voir aussi

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Questions fréquemment posées (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)