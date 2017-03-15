---
title: "LINQ to SQL Tools dans Visual Studio2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# LINQ to SQL Tools dans Visual Studio
LINQ to SQL a été la première technologie de mappage objet-relationnel publiée par Microsoft. Elle fonctionne bien dans les scénarios de base et continue à être pris en charge dans Visual Studio, mais il n’est plus en cours de développement actif. Utiliser LINQ to SQL lors de la maintenance d’une application héritée qui utilise déjà, ou dans des applications simples qui utilisent SQL Server et ne nécessitent pas de mappage de plusieurs table. En règle générale, les nouvelles applications doivent utiliser Entity Framework lorsqu’une couche mappeur relationnel objet est requise.  
  
 Dans Visual Studio, vous créez LINQ to SQL classes qui représentent des tables SQL à l’aide de la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 Le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] a deux zones distinctes sur son aire de conception : le volet d’entités sur la gauche et le volet de méthodes sur la droite. Le volet d'entités est l'aire de conception principale qui affiche les classes d'entité, associations et hiérarchies d'héritage. Le volet de méthodes est l’aire de conception qui affiche le <xref:System.Data.Linq.DataContext> méthodes qui sont mappées aux procédures stockées et fonctions.  
  
 Le [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]) fournit une aire de conception visuelle pour la création de [LINQ to SQL](../Topic/LINQ%20to%20SQL.md) classes d’entité et les associations (relations) basées sur des objets dans une base de données. En d'autres termes, le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] est utilisé pour créer, dans une application, un modèle objet qui effectue un mappage aux objets d'une base de données. Il génère également un fortement typé <xref:System.Data.Linq.DataContext> qui est utilisé pour envoyer et recevoir des données entre les classes d’entité et de la base de données. Le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] également fournit la fonctionnalité permettant de mapper des procédures stockées et des fonctions aux <xref:System.Data.Linq.DataContext> méthodes pour retourner des données et remplir des classes d’entité. Enfin, le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] donne la possibilité de concevoir des relations d'héritage entre des classes d'entité.  
  
## <a name="opening-the-or-designer"></a>Ouverture du Concepteur O/R  
 Pour ajouter un LINQ to SQL entity model à votre projet, choisissez **projet &#124 ; Ajouter un nouvel élément** puis  **Classes LINQ to SQL** dans la liste des éléments de projet :  
  
 ![Classes LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png "raddata LINQ to SQL Classes")  
  
 Visual Studio crée un fichier .dbml et l’ajoute à votre solution. C’est le fichier de mappage XML et ses fichiers de code associé.  
  
 ![Classes LINQ to SQL dans l’Explorateur de solutions](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata LINQ to SQL classes in Solution Explorer")  
  
 Lorsque vous sélectionnez le fichier .dbml, Visual Studio affiche l’aire du Concepteur O/R vous permet de créer visuellement le modèle. L’illustration suivante montre le concepteur après aient déplacé les tables Northwind Customers et Orders à partir de l’Explorateur de serveurs. Notez la relation entre les tables.  
  
 ![Concepteur LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png "raddata LINQ to SQL Designer")  
  
> [!IMPORTANT]
>  Le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] est un mappeur relationnel objet simple, car il prend en charge que les relations de mappage 1:1. En d'autres termes, une classe d'entité peut uniquement avoir une relation de mappage 1:1 avec une table ou une vue de base de données. Le mappage complexe, tel que le mappage d’une classe d’entité à une table jointe, n’est pas pris en charge ; utiliser Entity Framework pour le mappage complex. En outre, le concepteur est un générateur de code unidirectionnel. Cela signifie que seules les modifications apportées à l'aire du concepteur sont répercutées dans le fichier de code. Les modifications manuelles au fichier de code ne se sont pas répercutées dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Les modifications apportées manuellement dans le fichier de code sont remplacées lorsque le concepteur est enregistré et le code régénéré. Pour plus d’informations sur la façon d’ajouter le code utilisateur et d’étendre les classes générées par le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], consultez [Comment : étendre Code généré par le Concepteur O/R](../Topic/How%20to:%20Extend%20Code%20Generated%20by%20the%20O-R%20Designer.md).  
  
## <a name="creating-and-configuring-the-datacontext"></a>Création et configuration du DataContext  
 Après avoir ajouté un **Classes LINQ to SQL** élément à un projet et ouvrez le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], l’aire de conception vide représente vide <xref:System.Data.Linq.DataContext> prêt à être configuré. le <xref:System.Data.Linq.DataContext> est configuré avec les informations de connexion fournies par le premier élément glissé sur l’aire de conception... Par conséquent, le <xref:System.Data.Linq.DataContext> est configuré à l’aide des informations de connexion à partir du premier élément placé sur l’aire de conception. Pour plus d’informations sur la <xref:System.Data.Linq.DataContext> consultez classe [DataContext, méthodes (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Création des classes d'entité qui mappent aux tables et vues de base de données  
 Vous pouvez créer des classes d’entité mappées aux tables et vues en faisant glisser des tables de base de données et des vues de **Explorateur de serveurs**/**Explorateur de base de données** sur le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Comme indiqué dans la section précédente le <xref:System.Data.Linq.DataContext> est configuré avec les informations de connexion fournies par le premier élément glissé sur l’aire de conception. Si un élément suivant qui utilise une connexion différente est ajouté à la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], vous pouvez modifier la connexion pour le <xref:System.Data.Linq.DataContext>. Pour plus d’informations, consultez [Comment : créer des classes LINQ to SQL mappées aux tables et vues (Concepteur O/R)](../Topic/How%20to:%20Create%20LINQ%20to%20SQL%20classes%20mapped%20to%20tables%20and%20views%20\(O-R%20Designer\).md).  
  
## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Création des méthodes DataContext qui appellent des procédures stockées et des fonctions  
 Vous pouvez créer <xref:System.Data.Linq.DataContext> méthodes qui appellent (sont mappées à) des procédures stockées et fonctions en les faisant glisser à partir de **Explorateur de serveurs**/**Explorateur de base de données** sur le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Les procédures stockées et fonctions sont ajoutées à la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] en tant que méthodes de le <xref:System.Data.Linq.DataContext>.  
  
> [!NOTE]
>  Lorsque vous faites glisser des procédures stockées et des fonctions de **Explorateur de serveurs**/**Explorateur de base de données** sur le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], le type de retour généré <xref:System.Data.Linq.DataContext> méthode diffère selon l’endroit où vous placez l’élément. Pour plus d’informations, consultez [DataContext, méthodes (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configuration d'un DataContext pour utiliser des procédures stockées afin d'enregistrer les données entre des classes d'entité et une base de données  
 Comme indiqué précédemment, vous pouvez créer <xref:System.Data.Linq.DataContext> méthodes qui appellent des procédures stockées et des fonctions. En outre, vous pouvez assigner des procédures stockées qui peuvent être utilisées pour le comportement au moment de l'exécution par défaut de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] qui effectue les insertions, les mises à jour et les suppressions. Pour plus d’informations, consultez [Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="inheritance-and-the-or-designer"></a>Héritage et le Concepteur O/R  
 Comme d'autres objets, les classes [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] peuvent utiliser l'héritage et être dérivées d'autres classes. Dans une base de données, les relations d'héritage sont créées de plusieurs façons. Le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] prend en charge le concept d'héritage à table unique tel qu'il est souvent implémenté dans les systèmes relationnels. Pour plus d’informations, consultez [Comment : configurer l’héritage à l’aide du Concepteur O/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).  
  
## <a name="linq-to-sql-queries"></a>Requêtes LINQ to SQL  
 Les classes d’entité créés par le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] sont conçus pour une utilisation avec [LINQ (Language-Integrated Query)](../Topic/LINQ%20\(Language-Integrated%20Query\).md). Pour plus d’informations, consultez [Comment : demander des informations](../Topic/How%20to:%20Query%20for%20Information.md).  
  
## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Séparation du GeneratedDataContext et du code de classe d'entité dans des espaces de noms différents  
 Le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] fournit le **contexte Namespace** et **Entity Namespace** propriétés sur le <xref:System.Data.Linq.DataContext>. Ces propriétés déterminent dans quel espace de noms du <xref:System.Data.Linq.DataContext> et le code de classe d’entité est généré. Par défaut, ces propriétés sont vides et <xref:System.Data.Linq.DataContext> et les classes d’entité sont générés dans l’espace de noms de l’application. Pour générer le code dans un espace de noms autre que de l’espace de noms de l’application, entrez une valeur dans la **contexte Namespace** et/ou **Entity Namespace** Propriétés.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md)  
 Explique ce que <xref:System.Data.Linq.DataContext> méthodes sont et comment les créer.  
  
 [Héritage de classes de données (Concepteur O/R)](../data-tools/data-class-inheritance-o-r-designer.md)  
 Décrit le concept d'héritage de table unique et comment il est implémenté dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Comment : créer des LINQ to SQL classes mappées aux tables et vues (Concepteur O/R)](../Topic/How%20to:%20Create%20LINQ%20to%20SQL%20classes%20mapped%20to%20tables%20and%20views%20\(O-R%20Designer\).md)  
 Décrit comment créer des classes d'entité mappées aux tables et aux vues dans une base de données.  
  
 [Comment : créer une association (relation) entre les classes LINQ to SQL (Concepteur O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)  
 Décrit comment créer une relation entre des classes d'entité [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].  
  
 [Comment : créer des méthodes DataContext mappées aux procédures stockées et fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)  
 Décrit comment créer <xref:System.Data.Linq.DataContext> méthodes qui exécutent des procédures stockées ou fonctions lorsqu’elles sont appelées.  
  
 [Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
 Décrit comment configurer un <xref:System.Data.Linq.DataContext> pour utiliser des procédures stockées lors de l’enregistrement des données d’entité de classes dans une base de données.  
  
 [Comment : modifier le type de retour d’une méthode DataContext (Concepteur O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)  
 Décrit comment définir le type de retour d’un <xref:System.Data.Linq.DataContext> méthode pour le type d’une classe d’entité ou type généré automatiquement créé par le Concepteur O/R.  
  
 [Comment : ajouter la validation aux classes d’entité](../data-tools/how-to-add-validation-to-entity-classes.md)  
 Décrit comment générer des méthodes partielles qui permettent l'ajout de code pendant le changement de propriété et la mise à jour de classe d'entité.  
  
 [Comment : activer et désactiver (Concepteur O/R) pluralisation](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md)  
 Décrit comment activer et désactiver le changement de nom automatique des classes ajoutées au [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Comment : configurer l’héritage à l’aide du Concepteur O/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)  
 Décrit comment configurer des classes d'entité à l'aide de l'héritage à table unique avec le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Comment : étendre le Code généré par le Concepteur O/R](../Topic/How%20to:%20Extend%20Code%20Generated%20by%20the%20O-R%20Designer.md)  
 Décrit comment et où ajouter du code qui ne sera pas remplacé lors des modifications d'objets provoquant une régénération du code dans le Concepteur O/R.  
  
 [Procédure pas à pas : Création des Classes LINQ to SQL à l’aide de l’héritage de Table unique (Concepteur O/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)  
 Fournit des instructions pas à pas pour configurer des classes d'entité à l'aide de l'héritage à table unique avec le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Procédure pas à pas : Personnalisation de l’instruction insert, update et delete de comportement des classes d’entité](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
 Fournit des instructions pas à pas pour configurer un <xref:System.Data.Linq.DataContext> pour utiliser des procédures stockées lors de l’enregistrement des données d’entité de classes dans une base de données.  
  
## <a name="reference-content"></a>Contenu de référence  
 <xref:System.Linq>  
  
 <xref:System.Data.Linq>  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)   
 [Forum aux Questions](../Topic/Frequently%20Asked%20Questions.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [L’accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)