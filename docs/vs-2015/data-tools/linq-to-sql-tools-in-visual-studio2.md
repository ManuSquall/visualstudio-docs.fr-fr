---
title: Outils LINQ to SQL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 44e12e616e453dcdc0390e8a6eb5b2065a51a6bb
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59656932"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Outils LINQ to SQL dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

LINQ to SQL a été la première technologie de mapping objet-relationnel publiée par Microsoft. Il fonctionne bien dans les scénarios de base et continue à être pris en charge dans Visual Studio, mais il n’est plus en cours de développement. Utiliser LINQ to SQL lors de la mise à jour une application héritée qui utilise déjà, ou dans des applications simples qui utilisent SQL Server et ne nécessitent pas de mappage de plusieurs table. En règle générale, les nouvelles applications doivent utiliser Entity Framework lorsqu’une couche de Mappeur objet-relationnel est requise.

 Dans Visual Studio, vous créez LINQ to SQL des classes qui représentent des tables SQL à l’aide de la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 Le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] a deux zones distinctes sur son aire de conception : le volet d’entités sur la gauche et le volet de méthodes sur la droite. Le volet d'entités est l'aire de conception principale qui affiche les classes d'entité, associations et hiérarchies d'héritage. Le volet de méthodes est l’aire de conception qui affiche les méthodes <xref:System.Data.Linq.DataContext> mappées aux procédures stockées et aux fonctions.

 Le [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) fournit une aire de conception visuelle pour la création de [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) classes d’entité et les associations (relations) qui sont basées sur des objets dans une base de données. En d'autres termes, le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] est utilisé pour créer, dans une application, un modèle objet qui effectue un mappage aux objets d'une base de données. Il génère également un <xref:System.Data.Linq.DataContext> fortement typé utilisé pour envoyer et recevoir des données entre les classes d'entité et la base de données. Le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] fournit également des fonctionnalités permettant de mapper des procédures stockées et des fonctions aux méthodes <xref:System.Data.Linq.DataContext> afin de retourner des données et de remplir des classes d'entité. Enfin, le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] donne la possibilité de concevoir des relations d'héritage entre des classes d'entité.

## <a name="opening-the-or-designer"></a>Ouverture du Concepteur O/R
 Pour ajouter un LINQ à SQL entity model à votre projet, choisissez **projet &#124; ajouter un nouvel élément** , puis **Classes LINQ to SQL** dans la liste des éléments de projet :

 ![Classes LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png "raddata Classes LINQ to SQL")

 Visual Studio crée un fichier .dbml et l’ajoute à votre solution. C’est le fichier de mappage XML et ses fichiers de code connexes.

 ![Des classes LINQ to SQL dans l’Explorateur de solutions](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata LINQ to SQL classes dans l’Explorateur de solutions")

 Lorsque vous sélectionnez le fichier .dbml, Visual Studio affiche la surface du Concepteur O/R qui vous permet de créer visuellement le modèle. L’illustration suivante montre le concepteur une fois que les tables Northwind Customers et Orders ont été déplacés à partir de l’Explorateur de serveurs. Notez la relation entre les tables.

 ![Concepteur LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png "raddata concepteur LINQ to SQL")

> [!IMPORTANT]
>  Le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] est un mappeur relationnel objet simple, car il prend en charge uniquement les relations de mappage 1:1. En d'autres termes, une classe d'entité peut uniquement avoir une relation de mappage 1:1 avec une table ou une vue de base de données. Le mappage complexe, tel que le mappage d’une classe d’entité à une table jointe, n’est pas pris en charge ; utiliser Entity Framework pour le mappage complex. En outre, le concepteur est un générateur de code unidirectionnel. Cela signifie que seules les modifications apportées à l'aire du concepteur sont répercutées dans le fichier de code. Les modifications manuelles au fichier de code ne se sont pas répercutées dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Les modifications apportées manuellement dans le fichier de code sont remplacées lorsque le concepteur est enregistré et le code régénéré. Pour plus d’informations sur la façon d’ajouter le code utilisateur et d’étendre les classes générées par le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], consultez [Comment : Étendre le Code généré par le Concepteur O/R](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="creating-and-configuring-the-datacontext"></a>Création et configuration du DataContext
 Après avoir ajouté un **Classes LINQ to SQL** élément à un projet et ouvert le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], l’aire de conception vide représente vide <xref:System.Data.Linq.DataContext> prêt à être configuré. le <xref:System.Data.Linq.DataContext> est configuré avec les informations de connexion fournies par le premier élément glissé sur l’aire de conception... Par conséquent, <xref:System.Data.Linq.DataContext> est configuré en utilisant les informations de connexion du premier élément déposé sur l’aire de conception. Pour plus d’informations sur la <xref:System.Data.Linq.DataContext> , consultez classe [DataContext, méthodes (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Création des classes d'entité qui mappent aux tables et vues de base de données
 Vous pouvez créer des classes d’entité mappées aux tables et vues en faisant glisser des tables de base de données et les vues de **Explorateur de serveurs**/**Database Explorer** sur le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Comme indiqué dans la section précédente, <xref:System.Data.Linq.DataContext> est configuré avec les informations de connexion fournies par le premier élément glissé sur l'aire de conception. Si un élément suivant qui utilise une connexion différente est ajouté au [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], vous pouvez modifier la connexion pour le <xref:System.Data.Linq.DataContext>. Pour plus d'informations, voir [Procédure : créer des classes LINQ to SQL mappées à des tables et à des vues (Concepteur O/R)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Création des méthodes DataContext qui appellent des procédures stockées et des fonctions
 Vous pouvez créer <xref:System.Data.Linq.DataContext> méthodes qui appellent (sont mappées à) des procédures stockées et fonctions en les faisant glisser à partir de **Explorateur de serveurs**/**Database Explorer** sur la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Les procédures stockées et fonctions sont ajoutées au [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] comme méthodes du <xref:System.Data.Linq.DataContext>.

> [!NOTE]
>  Lorsque vous faites glisser des procédures stockées et des fonctions de **Explorateur de serveurs**/**Database Explorer** sur le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], le type de retour de généré <xref:System.Data.Linq.DataContext> diffère de la méthode selon l’endroit où vous placez l’élément. Pour plus d’informations, consultez [DataContext, méthodes (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configuration d'un DataContext pour utiliser des procédures stockées afin d'enregistrer les données entre des classes d'entité et une base de données
 Comme mentionné précédemment, vous pouvez créer des méthodes <xref:System.Data.Linq.DataContext> qui appellent des procédures stockées et des fonctions. En outre, vous pouvez assigner des procédures stockées qui peuvent être utilisées pour le comportement au moment de l'exécution par défaut de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] qui effectue les insertions, les mises à jour et les suppressions. Pour plus d'informations, voir [Procédure : affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Héritage et le Concepteur O/R
 Comme d'autres objets, les classes [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] peuvent utiliser l'héritage et être dérivées d'autres classes. Dans une base de données, les relations d'héritage sont créées de plusieurs façons. Le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] prend en charge le concept d'héritage à table unique tel qu'il est souvent implémenté dans les systèmes relationnels. Pour plus d'informations, voir [Procédure : configurer l’héritage à l’aide du Concepteur O/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Requêtes LINQ to SQL
 Les classes d’entité créées par le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] sont conçus pour une utilisation avec [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d). Pour plus d'informations, voir [Procédure : Demander des informations](http://msdn.microsoft.com/library/e538d288-2070-40ca-9da6-4fbc68cd6ad0).

## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Séparation du GeneratedDataContext et du code de classe d'entité dans des espaces de noms différents
 Le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] fournit le **contexte Namespace** et **Entity Namespace** propriétés sur le <xref:System.Data.Linq.DataContext>. Ces propriétés déterminent dans quel espace de noms le <xref:System.Data.Linq.DataContext> et le code de classe entité est généré. Par défaut, ces propriétés sont vides, les <xref:System.Data.Linq.DataContext> et les classes d'entité étant générés dans l'espace de noms de l'application. Pour générer le code dans un espace de noms autre que l’espace de noms de l’application, entrez une valeur dans les propriétés **Espace de noms du contexte** et/ou **Espace de noms de l’entité**.

## <a name="in-this-section"></a>Dans cette section
 [Méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md) explique ce que vous <xref:System.Data.Linq.DataContext> méthodes sont et comment les créer.

 [Classe de données d’héritage (Concepteur O/R)](../data-tools/data-class-inheritance-o-r-designer.md) décrit le concept d’héritage à table unique et comment il est implémenté dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Guide pratique pour Créer des LINQ to SQL classes mappées aux tables et vues (Concepteur O/R)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md) explique comment créer des classes d’entité qui sont mappées aux tables et vues dans une base de données.

 [Guide pratique pour Créer une association (relation) entre les classes LINQ to SQL (Concepteur O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) décrit comment créer une relation entre [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] classes d’entité.

 [Guide pratique pour Créer des méthodes DataContext mappées aux procédures stockées et fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) décrit comment créer <xref:System.Data.Linq.DataContext> méthodes qui exécutent des procédures stockées ou fonctions lorsqu’elles sont appelées.

 [Guide pratique pour Assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) explique comment configurer un <xref:System.Data.Linq.DataContext> pour utiliser des procédures stockées lors de l’enregistrement de données à partir de l’entité de classes dans une base de données.

 [Guide pratique pour Modifier le type de retour d’une méthode DataContext (Concepteur O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md) explique comment définir le type de retour d’un <xref:System.Data.Linq.DataContext> méthode soit le type d’une classe d’entité ou un type généré automatiquement créé par le Concepteur O/R.

 [Guide pratique pour Ajouter une validation aux classes d’entité](../data-tools/how-to-add-validation-to-entity-classes.md) décrit comment générer des méthodes partielles qui permettent l’ajout de code au cours des modifications de propriété et les mises à jour de la classe entity.

 [Guide pratique pour Activer et désactiver (Concepteur O/R) la pluralisation](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md) décrit comment activer et désactiver le changement de nom automatique des classes qui sont ajoutés à la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Guide pratique pour Configurer l’héritage à l’aide du Concepteur O/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) décrit comment configurer des classes d’entité à l’aide de l’héritage à table unique avec le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Guide pratique pour Étendre le Code généré par le Concepteur O/R](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md) décrit comment et où ajouter du code qui ne sera pas remplacé lorsque les modifications apportées aux objets dans le Concepteur O/R régénérer le code.

 [Procédure pas à pas : Création des Classes LINQ to SQL par héritage à Table unique à l’aide de (Concepteur O/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) fournit des instructions détaillées pour la configuration des classes d’entité à l’aide de l’héritage à table unique avec le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Procédure pas à pas : Personnalisation de l’insertion, mise à jour et supprimer le comportement des classes d’entité](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) fournit des instructions détaillées pour configurer un <xref:System.Data.Linq.DataContext> pour utiliser des procédures stockées lors de l’enregistrement de données à partir de l’entité de classes dans une base de données.

## <a name="reference-content"></a>Contenu de référence
 <xref:System.Linq>

 <xref:System.Data.Linq>

## <a name="see-also"></a>Voir aussi
 [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) [Forum aux Questions](http://msdn.microsoft.com/library/252ed666-0679-4eea-b71b-2f14117ef443) [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [l’accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
