---
title: Vue d’ensemble de Visual Studio le Concepteur O/R
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: acb279780db1291d62cde8202268e0990a56ea64
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>LINQ to SQL des outils dans Visual Studio

LINQ to SQL a été la première technologie de mappage relationnel objet publiée par Microsoft. Elle fonctionne bien dans les scénarios de base et continue à être pris en charge dans Visual Studio, mais il n’est plus en cours de développement actif. Utilisez LINQ SQL lors de la gestion d’une application héritée qui utilise déjà, ou dans des applications simples qui utilisent SQL Server et ne nécessitent pas de mappage de plusieurs table. En règle générale, les nouvelles applications doivent utiliser Entity Framework lorsqu’une couche de Mappeur objet / relationnel est requise.

Dans Visual Studio, vous créez LINQ to SQL classes qui représentent des tables SQL à l’aide du concepteur objet/relationnel (Concepteur O/R).

Le Concepteur O/R a deux zones distinctes sur son aire de conception : le volet d’entités sur la gauche et le volet de méthodes sur la droite. Le volet d'entités est l'aire de conception principale qui affiche les classes d'entité, associations et hiérarchies d'héritage. Le volet de méthodes est l’aire de conception qui affiche le <xref:System.Data.Linq.DataContext> les méthodes qui sont mappées aux procédures stockées et fonctions.

Le Concepteur O/R fournit une aire de conception visuelle pour la création de [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) des classes d’entité et les associations (relations) qui sont basées sur des objets dans une base de données. En d’autres termes, le Concepteur O/R est utilisé pour créer un modèle d’objet dans une application qui est mappé à des objets dans une base de données. Il génère également un <xref:System.Data.Linq.DataContext> fortement typé utilisé pour envoyer et recevoir des données entre les classes d'entité et la base de données. Le Concepteur O/R également fournit les fonctionnalités permettant de mapper des procédures stockées et des fonctions à <xref:System.Data.Linq.DataContext> méthodes pour retourner des données et remplir des classes d’entité. Enfin, le Concepteur O/R fournit la possibilité de concevoir des relations d’héritage entre classes d’entité.

## <a name="open-the-or-designer"></a>Ouvrez le Concepteur O/R

Pour ajouter un LINQ to SQL entity model à votre projet, choisissez **projet** > **ajouter un nouvel élément**, puis sélectionnez **Classes LINQ to SQL** dans la liste des éléments de projet :

![Classes LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio crée un fichier .dbml et l’ajoute à votre solution. C’est le fichier de mappage XML et ses fichiers de code associé.

![Classes LINQ to SQL dans l’Explorateur de solutions](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

Lorsque vous sélectionnez le fichier .dbml, Visual Studio affiche l’aire du Concepteur O/R qui vous permet de créer visuellement le modèle. L’illustration suivante montre le concepteur une fois que les tables Northwind Customers et Orders ont été déplacés à partir de l’Explorateur de serveurs. Notez la relation entre les tables.

![Concepteur LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> Le Concepteur O/R est un mappeur relationnel objet simple, car il prend en charge que les relations de mappage 1:1. En d'autres termes, une classe d'entité peut uniquement avoir une relation de mappage 1:1 avec une table ou une vue de base de données. Le mappage complexe, tel que le mappage d’une classe d’entité à une table jointe, n’est pas prise en charge ; utilisez Entity Framework pour le mappage complex. En outre, le concepteur est un générateur de code unidirectionnel. Cela signifie que seules les modifications apportées à l'aire du concepteur sont répercutées dans le fichier de code. Les modifications manuelles apportées au fichier de code ne sont pas répercutées dans le Concepteur O/R. Les modifications apportées manuellement dans le fichier de code sont remplacées lorsque le concepteur est enregistré et le code régénéré. Pour plus d’informations sur la façon d’ajouter le code utilisateur et d’étendre les classes générées par le Concepteur O/R, consultez [Comment : étendre Code généré par le Concepteur O/R](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>Créer et configurer le DataContext

Après avoir ajouté un **Classes LINQ to SQL** d’élément à un projet et ouvrez le Concepteur O/R, l’aire de conception vide représente vide <xref:System.Data.Linq.DataContext> prêt à être configuré. le <xref:System.Data.Linq.DataContext> est configuré avec les informations de connexion fournies par le premier élément qui est déplacé vers l’aire de conception... Par conséquent, le <xref:System.Data.Linq.DataContext> est configuré à l’aide des informations de connexion à partir du premier élément déposé sur l’aire de conception. Pour plus d’informations sur la <xref:System.Data.Linq.DataContext> , consultez classe [des méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Créer des classes d’entité qui mappent aux tables de base de données et des vues

Vous pouvez créer des classes d’entité mappées aux tables et des vues en faisant glisser des tables de base de données et des vues de **l’Explorateur de serveurs**/**l’Explorateur de base de données** sur le Concepteur O/R. Comme indiqué dans la section précédente, <xref:System.Data.Linq.DataContext> est configuré avec les informations de connexion fournies par le premier élément glissé sur l'aire de conception. Si un élément suivant qui utilise une autre connexion est ajouté au Concepteur O/R, vous pouvez modifier la connexion pour le <xref:System.Data.Linq.DataContext>. Pour plus d’informations, consultez [Comment : créer des classes LINQ to SQL mappées aux tables et vues (Concepteur O/R)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Créer des méthodes DataContext qui appellent des procédures stockées et fonctions

Vous pouvez créer <xref:System.Data.Linq.DataContext> des méthodes qui appellent (sont mappées à) fonctions et procédures stockées en les faisant glisser à partir de **l’Explorateur de serveurs**/**l’Explorateur de base de données** sur le Concepteur O/R. Procédures stockées et fonctions sont ajoutées au Concepteur O/R en tant que méthodes de le <xref:System.Data.Linq.DataContext>.

> [!NOTE]
> Lorsque vous faites glisser des procédures stockées et des fonctions de **l’Explorateur de serveurs**/**l’Explorateur de base de données** sur le Concepteur O/R, le type de retour généré <xref:System.Data.Linq.DataContext> diffère de la méthode selon l’endroit où vous déposez l’élément. Pour plus d’informations, consultez [des méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configurer un DataContext pour utiliser des procédures stockées pour enregistrer des données entre les classes d’entité et une base de données

Comme mentionné précédemment, vous pouvez créer des méthodes <xref:System.Data.Linq.DataContext> qui appellent des procédures stockées et des fonctions. En outre, vous pouvez également affecter les procédures stockées qui peuvent être utilisés pour la valeur par défaut LINQ au comportement d’exécution SQL qui effectue des insertions, mises à jour et les suppressions. Pour plus d’informations, consultez [Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>L’héritage et le Concepteur O/R

Comme d’autres objets, classes LINQ to SQL peut utiliser l’héritage et être dérivée d’autres classes. Dans une base de données, les relations d'héritage sont créées de plusieurs façons. Le Concepteur O/R prend en charge le concept d’héritage à table unique tel qu’il est souvent implémenté dans les systèmes relationnels. Pour plus d’informations, consultez [Comment : configurer l’héritage à l’aide du Concepteur O/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Requêtes LINQ to SQL

Les classes d’entité créés par le Concepteur O/R sont conçus pour une utilisation avec [Language-Integrated Query (LINQ)](/dotnet/csharp/linq/). Pour plus d’informations, consultez [Comment : demander des informations](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Séparer le code de classe DataContext et entité généré dans différents espaces de noms

Le Concepteur O/R fournit la **contexte Namespace** et **Entity Namespace** propriétés sur le <xref:System.Data.Linq.DataContext>. Ces propriétés déterminent dans quel espace de noms le <xref:System.Data.Linq.DataContext> et le code de classe entité est généré. Par défaut, ces propriétés sont vides, les <xref:System.Data.Linq.DataContext> et les classes d'entité étant générés dans l'espace de noms de l'application. Pour générer le code dans un espace de noms autre que de l’espace de noms de l’application, entrez une valeur dans la **contexte Namespace** et/ou **Entity Namespace** propriétés.

## <a name="reference-content"></a>Contenu de référence

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Voir aussi

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Forum aux Questions (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)