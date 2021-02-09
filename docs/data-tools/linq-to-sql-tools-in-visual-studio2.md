---
title: Vue d’ensemble du concepteur LINQ to SQL O/R
description: Découvrez une vue d’ensemble des outils de LINQ to SQL dans Visual Studio. En savoir plus sur le Concepteur Objet Relationnel (Concepteur O/R).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 20473125814b1ee0569579c7248b7b940cd31500
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858642"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Outils LINQ to SQL dans Visual Studio

LINQ to SQL était la première technologie de mappage relationnel objet publiée par Microsoft. Il fonctionne bien dans les scénarios de base et continue d’être pris en charge dans Visual Studio, mais il n’est plus en cours de développement actif. Utilisez LINQ to SQL lors de la maintenance d’une application héritée qui l’utilise déjà, ou dans des applications simples qui utilisent SQL Server et ne nécessitent pas de mappage de tables multiples. En règle générale, les nouvelles applications doivent utiliser le Entity Framework lorsqu’une couche de mappage objet-relationnel est requise.

## <a name="install-the-linq-to-sql-tools"></a>Installer les outils de LINQ to SQL

Dans Visual Studio, vous créez LINQ to SQL classes qui représentent des tables SQL à l’aide de la **Concepteur Objet Relationnel** (**Concepteur O/R**). Le Concepteur O/R est l’interface utilisateur permettant de modifier les fichiers. dbml. La modification de fichiers. dbml avec une aire de conception nécessite les outils de LINQ to SQL qui ne sont pas installés par défaut dans le cadre de l’une des charges de travail de Visual Studio.

Pour installer les outils de LINQ to SQL, démarrez le programme d’installation de Visual Studio, choisissez **modifier**, sélectionnez l’onglet **composants individuels** , puis sélectionnez **LINQ to SQL outils** sous la catégorie **outils de code** .

## <a name="what-is-the-or-designer"></a>Qu’est-ce que le Concepteur O/R ?

Le **Concepteur O/R** a deux zones distinctes sur l’aire de conception : le volet entités à gauche et le volet méthodes à droite. Le volet d'entités est l'aire de conception principale qui affiche les classes d'entité, associations et hiérarchies d'héritage. Le volet de méthodes est l’aire de conception qui affiche les méthodes <xref:System.Data.Linq.DataContext> mappées aux procédures stockées et aux fonctions.

Le **Concepteur O/R** fournit une aire de conception visuelle pour créer des [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) des classes d’entité et des associations (relations) basées sur des objets dans une base de données. En d’autres termes, le **Concepteur O/R** crée un modèle objet dans une application qui mappe aux objets dans une base de données. Elle génère également un fortement typé <xref:System.Data.Linq.DataContext> qui envoie et reçoit des données entre les classes d’entité et la base de données. Le **Concepteur O/R** fournit également des fonctionnalités permettant de mapper des procédures stockées et des fonctions aux <xref:System.Data.Linq.DataContext> méthodes pour retourner des données et remplir des classes d’entité. Enfin, le **Concepteur O/R** offre la possibilité de concevoir des relations d’héritage entre des classes d’entité.

## <a name="open-the-or-designer"></a>Ouvrir le Concepteur O/R

Pour ajouter un modèle d’entité LINQ to SQL à votre projet, choisissez **projet**  >  **Ajouter un nouvel élément**, puis sélectionnez **LINQ to SQL classes** dans la liste des éléments de projet :

![Classes LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio crée un fichier *. dbml* et l’ajoute à votre solution. Il s’agit du fichier de mappage XML et de ses fichiers de code associés.

![Classes LINQ to SQL dans Explorateur de solutions](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

Lorsque vous sélectionnez le fichier *. dbml* , Visual Studio affiche l’aire du **Concepteur O/R** qui vous permet de créer visuellement le modèle. L’illustration suivante montre le concepteur après que les `Customers` tables Northwind et `Orders` ont été déplacées à partir de **Explorateur de serveurs**. Notez la relation entre les tables.

![Concepteur LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> Le **Concepteur O/R** est un mappeur relationnel objet simple, car il ne prend en charge que les relations de mappage 1:1. En d'autres termes, une classe d'entité peut uniquement avoir une relation de mappage 1:1 avec une table ou une vue de base de données. Le mappage complexe, tel que le mappage d’une classe d’entité à une table jointe, n’est pas pris en charge ; Utilisez la Entity Framework pour le mappage complexe. En outre, le concepteur est un générateur de code unidirectionnel. Cela signifie que seules les modifications apportées à l'aire du concepteur sont répercutées dans le fichier de code. Les modifications manuelles apportées au fichier de code ne sont pas reflétées dans le **Concepteur O/R**. Les modifications apportées manuellement dans le fichier de code sont remplacées lorsque le concepteur est enregistré et le code régénéré. Pour plus d’informations sur la façon d’ajouter le code utilisateur et d’étendre les classes générées par le **Concepteur O/R**, consultez [Comment : étendre le code généré par le Concepteur O/R](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>Créer et configurer DataContext

Une fois que vous avez ajouté un élément **LINQ to SQL classes** à un projet et ouvert le **Concepteur O/R**, l’aire de conception vide représente un vide <xref:System.Data.Linq.DataContext> prêt à être configuré. Le <xref:System.Data.Linq.DataContext> est configuré avec les informations de connexion fournies par le premier élément glissé sur l’aire de conception. Par conséquent, <xref:System.Data.Linq.DataContext> est configuré en utilisant les informations de connexion du premier élément déposé sur l’aire de conception. Pour plus d’informations sur la <xref:System.Data.Linq.DataContext> classe, consultez [méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Créer des classes d’entité qui mappent à des vues et des tables de base de données

Vous pouvez créer des classes d’entité mappées à des tables et des vues en faisant glisser des tables et des vues de base de données à partir de **Explorateur de serveurs** ou **Explorateur de base de données** vers le **Concepteur O/R**. Comme indiqué dans la section précédente, <xref:System.Data.Linq.DataContext> est configuré avec les informations de connexion fournies par le premier élément glissé sur l’aire de conception. Si un élément suivant qui utilise une connexion différente est ajouté au **Concepteur O/R**, vous pouvez modifier la connexion pour le <xref:System.Data.Linq.DataContext> . Pour plus d’informations, consultez [Comment : créer des classes LINQ to SQL mappées à des tables et des vues (Concepteur O/R)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Créer des méthodes DataContext qui appellent des procédures stockées et des fonctions

Vous pouvez créer des <xref:System.Data.Linq.DataContext> méthodes qui appellent (sont mappées à) des procédures stockées et des fonctions en les faisant glisser de **Explorateur de serveurs** ou **Explorateur de base de données** vers le **Concepteur O/R**. Les procédures stockées et les fonctions sont ajoutées au **Concepteur O/R** en tant que méthodes de <xref:System.Data.Linq.DataContext> .

> [!NOTE]
> Lorsque vous faites glisser des procédures stockées et des fonctions de **Explorateur de serveurs** ou **Explorateur de base de données** vers le **Concepteur O/R**, le type de retour de la <xref:System.Data.Linq.DataContext> méthode générée diffère selon l’endroit où vous déposez l’élément. Pour plus d’informations, consultez [méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configurer un DataContext pour utiliser des procédures stockées pour enregistrer des données entre des classes d’entité et une base de données

Comme mentionné précédemment, vous pouvez créer des méthodes <xref:System.Data.Linq.DataContext> qui appellent des procédures stockées et des fonctions. En outre, vous pouvez également assigner des procédures stockées qui sont utilisées pour le comportement par défaut LINQ to SQL au moment de l’exécution, qui effectue des insertions, des mises à jour et des suppressions. Pour plus d’informations, consultez [Comment : assigner des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Héritage et Concepteur O/R

Comme d’autres objets, les classes LINQ to SQL peuvent utiliser l’héritage et être dérivées d’autres classes. Dans une base de données, les relations d'héritage sont créées de plusieurs façons. Le **Concepteur O/R** prend en charge le concept d’héritage de table unique, car il est souvent implémenté dans les systèmes relationnels. Pour plus d’informations, consultez [Comment : configurer l’héritage à l’aide du Concepteur O/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Requêtes LINQ to SQL

Les classes d’entité créées par le **Concepteur O/R** sont conçues pour une utilisation avec [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/). Pour plus d’informations, consultez [Comment : interroger pour obtenir des informations](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Séparer le DataContext et le code de la classe d’entité générés dans des espaces de noms différents

Le **Concepteur O/R** fournit les propriétés **espace de noms de contexte** et espace de noms d' **entité** sur le <xref:System.Data.Linq.DataContext> . Ces propriétés déterminent dans quel espace de noms le <xref:System.Data.Linq.DataContext> et le code de classe entité est généré. Par défaut, ces propriétés sont vides, les <xref:System.Data.Linq.DataContext> et les classes d'entité étant générés dans l'espace de noms de l'application. Pour générer le code dans un espace de noms autre que l’espace de noms de l’application, entrez une valeur dans les propriétés **Espace de noms du contexte** et/ou **Espace de noms de l’entité**.

## <a name="reference-content"></a>Contenu de référence

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Voir aussi

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Forum aux questions (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)
