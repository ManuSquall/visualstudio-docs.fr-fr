---
title: "Utilisation de groupes de donn&#233;es dans Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.data.DataSet"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "cache (Visual Studio), groupes de données"
  - "respect de la casse, groupes de données"
  - "enregistrements enfants"
  - "contraintes (Visual Basic), groupes de données"
  - "enregistrement actif dans le groupe de données"
  - "adaptateurs de données, remplir des groupes de données"
  - "mise en mémoire cache des données, groupes de données"
  - "relations de données"
  - "bases de données (Visual Basic), mettre à jour"
  - "DataRelation (objet), groupes de données"
  - "DataSet (classe)"
  - "DataSet (classe), à propos des groupes de données"
  - "groupes de données (Visual Basic)"
  - "groupes de données (Visual Basic), propriétés étendues"
  - "groupes de données (Visual Basic), remplir"
  - "groupes de données (Visual Basic), msprop"
  - "groupes de données (Visual Basic), namespace"
  - "groupes de données (Visual Basic), remplir"
  - "groupes de données (Visual Basic), relations"
  - "propriétés étendues, dans les datasets typés"
  - "clés externes, groupes de données"
  - "tables maître/détail, groupes de données"
  - "msprop"
  - "enregistrements parents dans des groupes de données"
  - "tables connexes"
  - "tables connexes, groupes de données"
  - "relations, groupes de données"
  - "schémas (Visual Basic), groupes de données"
  - "datasets typés"
  - "datasets typés, comparaison avec les datasets non typés"
  - "contraintes uniques (groupes de données)"
  - "datasets non typés"
  - "datasets non typés, comparaison avec les datasets typés"
  - "mise à jour de groupes de données, à propos des mises à jour de groupes de données"
  - "XML (Visual Basic), groupes de données"
  - "schémas XML, à propos des groupes de données et des schémas XML"
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
caps.latest.revision: 49
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Utilisation de groupes de donn&#233;es dans Visual Studio
Les groupes de données sont des objets qui contiennent des tables de données dans lesquelles pouvez stocker temporairement des données en vue de les utiliser dans votre application.  Si votre application doit utiliser des données, vous pouvez charger les données dans un groupe de données. Votre application dispose ainsi d'un cache local en mémoire des données à utiliser.  Vous pouvez utiliser les données contenues dans un groupe de données même si votre application est déconnectée de la base de données.  Le groupe de données conserve des informations sur les modifications apportées à ses données afin d'assurer le suivi des mises à jour et leur renvoi à la base de données dès que votre application est reconnectée.  
  
 Les rubriques suivantes fournissent des détails sur l'utilisation des groupes de données dans Visual Studio :  
  
|Rubrique|Description|  
|--------------|-----------------|  
|[Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)|Fournit une explication des outils au moment du design pour créer des groupes de données.|  
|[Comment : créer un groupe de données typé](../data-tools/create-and-configure-datasets-in-visual-studio.md)|Explique comment créer un groupe de données typé à l'aide d'outils de conception dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Comment : étendre les fonctionnalités d'un groupe de données](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)|Fournit la procédure de création d'une classe partielle pour le groupe de données auquel vous pouvez ajouter du code en plus de code généré par concepteur.|  
|[Comment : ouvrir un groupe de données dans le Concepteur de DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)|Explique comment ouvrir des groupes de données depuis l'**Explorateur de solutions** et la fenêtre **Sources de données**.|  
|[Comment : modifier un groupe de données](../Topic/How%20to:%20Edit%20a%20Dataset.md)|Explique comment modifier les objets contenus dans un groupe de données à l'aide du **Concepteur de DataSet**.|  
|[Procédure pas à pas : création d'un groupe de données avec le Concepteur de DataSet](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)|Fournit des instructions pas à pas pour la création d'un groupe de données typé sans l'aide de l'**Assistant Configuration de source de données**.|  
|[Conception de DataTables](../data-tools/designing-datatables.md)|Fournit des liens vers des rubriques qui expliquent comment créer et modifier des tables de données avec les outils au moment du design.|  
|[Relations dans les groupes de données](../data-tools/relationships-in-datasets.md)|Fournit des liens vers des rubriques qui expliquent comment créer et modifier des relations de données avec les outils au moment du design.|  
|[TableAdapters](../Topic/TableAdapters.md)|Fournit des liens vers des rubriques qui expliquent comment créer et modifier des TableAdapters avec les outils au moment du design.|  
|[Utilisation de groupes de données dans des applications multicouches](../data-tools/work-with-datasets-in-n-tier-applications.md)|Explique ce que sont les applications multicouches et quelles fonctionnalités peuvent être utilisées avec des groupes de données dans ces applications.|  
  
 La structure d'un <xref:System.Data.DataSet> est similaire à celle d'une base de données relationnelle : elle expose un modèle objet hiérarchique constitué de tables, de lignes, de colonnes, de contraintes et de relations.  
  
 Les groupes de données peuvent être typés ou non typés.  \(Pour plus d'informations, consultez la section suivante intitulée « datasets typés et non typés »\). Les datasets typés dérivent leur schéma \(structure de tables et de colonnes\) de fichiers .xsd et sont plus faciles à programmer.  Vous pouvez utiliser des groupes de données typés ou non dans vos applications.  Toutefois, Visual Studio propose davantage d'outils prenant en charge les groupes de données typés ; en outre, la programmation avec ceux\-ci est plus simple et moins sujette aux erreurs.  
  
 Vous pouvez créer des groupes de données typés en exécutant l'[Configuration de source de données \(Assistant\)](../data-tools/media/data-source-configuration-wizard.png) ou en ajoutant un élément **DataSet** à l'aide de la commande **Ajouter un nouvel élément** du menu **Projet**.  Pour plus d'informations, consultez [Comment : créer un groupe de données typé](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
 Créez des groupes de données non typés en faisant glisser des éléments **Groupe de données** de la **Boîte à outils** jusqu'au [Windows Forms Designer](http://msdn.microsoft.com/fr-fr/3c3d61f8-f36c-4d41-b9c3-398376fabb15) ou [Component Designer](../Topic/Component%20Designer.md).  
  
 Lorsque vous avez créé des groupes de données, modifiez\-les dans le [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md).  
  
 Vous pouvez créer et utiliser des groupes de données typés et non typés à l'aide des parties suivantes des espaces de noms du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 ![Espace de noms de groupes de données de données système](../data-tools/media/vbdatasetnamspace.png "vbDataSetNamspace")  
Les groupes de données se trouvent dans l'espace de noms System.Data  
  
 Les objets d'un groupe de données vous sont exposés par le biais de constructions de programmation standard telles que propriétés et collections.  Par exemple :  
  
-   La classe <xref:System.Data.DataSet> inclut la collection <xref:System.Data.DataTableCollection> de tables de données et la collection <xref:System.Data.DataRelationCollection> d'objets <xref:System.Data.DataRelation>.  
  
-   La classe <xref:System.Data.DataTable> inclut la collection <xref:System.Data.DataRowCollection> de lignes de table, la collection <xref:System.Data.DataColumnCollection> de colonnes de données, ainsi que les collections <xref:System.Data.DataTable.ChildRelations%2A> et <xref:System.Data.DataTable.ParentRelations%2A> de relations de données.  
  
-   La classe <xref:System.Data.DataRow> inclut la propriété <xref:System.Data.DataRow.RowState%2A> dont les valeurs indiquent si la ligne a été modifiée depuis que la table de données a été chargée pour la première fois à partir de la base de données et si tel est le cas, comment elle a été modifiée.  Les valeurs possibles pour la propriété <xref:System.Data.DataRow.RowState%2A> incluent <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> et <xref:System.Data.DataRowState>.  
  
## Remplissage des groupes de données avec des données  
 Un groupe de données ne contient aucune donnée réelle par défaut.  Le remplissage d'un groupe de données avec des données fait en réalité référence au chargement de données dans les objets <xref:System.Data.DataTable> qui composent le groupe de données.  Pour remplir les tables de données, vous devez exécuter des requêtes TableAdapter, ou des commandes d'adaptateur de données \(par exemple, <xref:System.Data.SqlClient.SqlDataAdapter>\).  Lorsque vous remplissez de données un groupe de données, divers événements sont déclenchés, des contraintes sont contrôlées, etc.  Pour plus d'informations sur le chargement de données dans un groupe de données, consultez [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md).  
  
 Le code permettant de remplir un groupe de données est ajouté automatiquement au gestionnaire d'événements de chargement de formulaire lorsque vous faites glisser des éléments depuis la [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md) jusqu'à un formulaire dans votre application Windows.  Pour plus d'informations, exécutez la procédure pas à pas suivante : [Procédure pas à pas : affichage de données sur un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).  
  
 Exemple de remplissage d'un groupe de données à l'aide d'un TableAdapter :  
  
 [!CODE [VbRaddataDatasets#1](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#1)]  
  
 Vous pouvez remplir un groupe de données de différentes manières :  
  
-   Si vous avez créé le groupe de données à l'aide d'outils au moment du design, tels que l'un des Assistants de données, appelez la méthode `Fill` d'un TableAdapter.  \(Les TableAdapters sont créés à l'aide d'une méthode `Fill` par défaut, mais vous avez la possibilité de modifier leur nom ; par conséquent, le nom réel de la méthode peut être différent.\) Pour plus d'informations, consultez la section « Remplissage d'un groupe de données à l'aide d'un TableAdapter » de la rubrique [Comment : remplir de données un groupe de données](../data-tools/how-to-fill-a-dataset-with-data.md).  
  
-   Appelez la méthode `Fill` d'un <xref:System.Data.Common.DataAdapter>.  Pour plus d'informations, consultez [Remplissage d'un DataSet à partir d'un DataAdapter](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md).  
  
-   Vous pouvez remplir manuellement les tables du groupe de données en créant des objets <xref:System.Data.DataRow> et en les ajoutant à la collection <xref:System.Data.DataRowCollection> de la table.  \(Vous ne pouvez recourir à cette méthode qu'au moment de l'exécution ; il est impossible de définir la collection <xref:System.Data.DataRowCollection> au moment du design.\) Pour plus d'informations, consultez [Ajout de données à un objet DataTable](../Topic/Adding%20Data%20to%20a%20DataTable.md).  
  
-   Vous pouvez lire un document ou un flux XML dans le groupe de données.  Pour plus d'informations, consultez la méthode <xref:System.Data.DataSet.ReadXml%2A>.  Pour obtenir un exemple, consultez [Procédure pas à pas : lecture des données XML dans un groupe de données](../data-tools/read-xml-data-into-a-dataset.md).  
  
-   Vous pouvez fusionner \(copier\) le contenu d'un groupe de données avec un autre.  Cette méthode peut être utile si votre application obtient des groupes de données de différentes sources \(différents services Web XML, par exemple\), mais qu'elle doit les consolider dans un seul et unique groupe de données.  Pour plus d'informations, consultez [Fusion du contenu d'un DataSet](../Topic/Merging%20DataSet%20Contents.md).  
  
-   Vous pouvez fusionner \(copier\) le contenu d'un <xref:System.Data.DataTable> avec un autre.  
  
## Enregistrement, dans une base de données, des données contenues dans un groupe de données  
 Lorsque des modifications sont apportées aux enregistrements du groupe de données, elles doivent également être reportées dans la base de données.  Pour reporter des modifications du groupe de données dans la base de données, vous devez appeler la méthode `Update` du TableAdapter ou du <xref:System.Data.Common.DataAdapter> qui communique entre le groupe de données et la base de données correspondante.  
  
 À l'aide des outils de conception de données Visual Studio, renvoyez les données à une base de données en appelant la méthode Update du TableAdapter et en passant la table de données que vous souhaitez enregistrer.  Par exemple :  
  
 [!CODE [VbRaddataDatasets#2](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#2)]  
  
 Pour un contrôle plus fin du processus de mise à jour, appelez une des méthodes DBDirect du TableAdapter dans laquelle vous pouvez passer des valeurs individuelles pour chaque ligne de données.  Pour plus d'informations, consultez [Comment : mettre à jour les données à l'aide d'un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) et [Procédure pas à pas : enregistrement des données avec les méthodes DBDirect du TableAdapter](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md).  
  
 La classe <xref:System.Data.DataRow> permettant de manipuler des enregistrements individuels inclut la propriété <xref:System.Data.DataRow.RowState%2A> dont les valeurs indiquent si la ligne a été modifiée depuis que la table de données a été chargée pour la première fois à partir de la base de données et si tel est le cas, comment elle a été modifiée.  Les valeurs possibles incluent <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> et <xref:System.Data.DataRowState>.  Les méthodes `Update` du TableAdapter et du <xref:System.Data.Common.DataAdapter> examinent la valeur de la propriété <xref:System.Data.DataRow.RowState%2A> pour identifier les enregistrements devant être écrits dans la base de données et la commande de base de données \(`InsertCommand`, `UpdateCommand` et `DeleteCommand`\) à appeler.  
  
 Pour plus d'informations sur la mise à jour de données, consultez [Enregistrement des données](../data-tools/saving-data.md).  
  
## Navigation au sein des enregistrements contenus dans des groupes de données  
 Parce qu'ils sont des conteneurs de données complètement déconnectés, les groupes de données \(à la différence des recordsets ADO\) ne prennent pas en charge le concept d'enregistrement en cours.  Au lieu de cela, tous les enregistrements du groupe de données sont disponibles à tout moment.  
  
 Comme la notion d'enregistrement en cours n'existe pas, aucune propriété spécifique ne pointe vers un enregistrement en cours et aucune méthode ou propriété ne permet de passer d'un enregistrement à un autre \(voir la remarque ci\-dessous\).  Vous pouvez accéder aux différentes tables d'un groupe de données en tant qu'objets ; chaque table expose une collection de lignes.  Vous pouvez traiter cette collection comme n'importe quelle autre en accédant aux lignes à l'aide de son index ou en utilisant des instructions propres aux collections dans votre langage de programmation.  
  
 Par exemple, vous pouvez obtenir la quatrième ligne de la table `Customers` avec le code suivant :  
  
 [!CODE [VbRaddataDatasets#3](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#3)]  
  
> [!NOTE]
>  Si vous liez des contrôles situés dans un formulaire à un groupe de données, vous pouvez utiliser le composant <xref:System.Windows.Forms.BindingNavigator> pour simplifier l'accès aux enregistrements individuels.  Pour plus d'informations, consultez [Comment : naviguer au sein des données dans les Windows Forms](../Topic/How%20to:%20Navigate%20Data%20in%20Windows%20Forms.md).  
  
## LINQ to DataSet  
 [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] active [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md) sur les données dans un objet <xref:System.Data.DataSet>.  Pour plus d'informations, consultez [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md).  
  
## Groupes de données et XML  
 Un groupe de données est un affichage relationnel des données pouvant être représentées en XML.  Grâce à elle, vous pouvez tirer profit des fonctionnalités suivantes des groupes de données :  
  
-   La structure d'un groupe de données \(ses tables, colonnes, relations et contraintes\) peut être définie dans un schéma XML.  Les groupes de données peuvent lire et écrire des schémas qui stockent des informations structurées à l'aide des méthodes <xref:System.Data.DataSet.ReadXmlSchema%2A> et <xref:System.Data.DataSet.WriteXmlSchema%2A>.  Si aucun schéma n'est disponible, le groupe de données peut en déduire un \(par le biais de sa méthode <xref:System.Data.DataSet.InferXmlSchema%2A>\) à partir des données d'un document XML présentant une structure relationnelle.  Pour plus d'informations sur les schémas XML, consultez [Création de schémas XML](../Topic/Building%20XML%20Schemas.md).  
  
-   Vous pouvez générer une classe DataSet qui incorpore des informations de schéma pour définir la structure de ses données.  Cela porte le nom de groupe de données *typé*.  Pour plus d'informations sur la création d'un groupe de données typé, consultez [Comment : créer un groupe de données typé](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
-   Vous pouvez lire un document ou un flux XML dans un groupe de données à l'aide de la méthode <xref:System.Data.DataSet.ReadXml%2A> du groupe de données et écrire un groupe de données au format XML à l'aide de la méthode <xref:System.Data.DataSet.WriteXml%2A>.  XML est un format d'échange standard des données entre différentes applications ; vous pouvez donc charger un groupe de données contenant des informations au format XML envoyées par d'autres applications.  De même, il est possible d'écrire les données d'un groupe de données sous la forme d'un document ou d'un flux XML qui pourra être partagé avec d'autres applications ou simplement stocké dans un format standard.  
  
-   Vous pouvez créer une vue XML \(un objet <xref:System.Xml.XmlDataDocument>\) du contenu d'un groupe de données ou d'une table de données, puis afficher et manipuler les données en faisant appel à des méthodes relationnelles \(par le biais du groupe de données\) ou à des méthodes XML.  Les deux vues sont automatiquement synchronisées lorsqu'elles sont modifiées.  
  
## Datasets typés et non typés  
 Un dataset typé est d'abord dérivé de la classe de base <xref:System.Data.DataSet>, puis utilise des informations provenant du **Concepteur de DataSet**, enregistrées dans un fichier .xsd, pour générer une nouvelle classe DataSet fortement typée.  Les informations provenant du schéma \(tables, colonnes, etc.\) sont générées et compilées dans cette nouvelle classe DataSet pour constituer un ensemble d'objets et de propriétés de premier plan.  Parce qu'un dataset typé hérite de la classe <xref:System.Data.DataSet> de base, la classe typée reprend toutes les fonctionnalités de la classe <xref:System.Data.DataSet> et peut être utilisée avec des méthodes acceptant comme paramètre une instance de classe <xref:System.Data.DataSet>.  
  
 En revanche, un dataset non typé ne possède pas de schéma intégré équivalent.  À l'instar d'un dataset typé, il contient des tables, des colonnes, etc., mais ceux\-ci ne sont exposés qu'en tant que collections.  \(Toutefois, après avoir créé manuellement les tables et autres éléments de données d'un dataset non typé, vous pouvez exporter la structure du groupe de données en tant que schéma à l'aide de sa méthode <xref:System.Data.DataSet.WriteXmlSchema%2A>.\)  
  
### Comparaison de l'accès aux données dans les groupes de données typés et non typés  
 La classe d'un groupe de données typé possède un modèle d'objet dans lequel ses propriétés prennent les noms réels des tables et colonnes.  Par exemple, si vous travaillez avec un groupe de données typé, vous pouvez référencer une colonne à l'aide d'un code pareil à celui\-ci :  
  
 [!CODE [VbRaddataDatasets#4](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#4)]  
  
 En revanche, si vous travaillez avec un groupe de données non typé, vous utiliserez le code équivalent suivant :  
  
 [!CODE [VbRaddataDatasets#5](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#5)]  
  
 L'accès typé est non seulement plus facile à lire, mais aussi entièrement pris en charge par IntelliSense dans l'**éditeur de code** de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Les groupes de données typés sont non seulement plus simples à manipuler, mais leur syntaxe permet de contrôler le type au moment de la compilation, ce qui réduit considérablement les risques d'erreur dans l'assignation des valeurs aux membres d'un groupe de données.  Si vous modifiez le nom d'une colonne dans votre <xref:System.Data.DataSet>, puis compilez votre application, une erreur de build se produit.  En double\-cliquant sur l'erreur de build dans la **Liste des tâches**, vous pouvez accéder directement à la ligne ou aux lignes de code qui référencent l'ancien nom de colonne.  L'accès aux tables et aux colonnes d'un groupe de données typé est également légèrement plus rapide au moment de l'exécution, parce qu'il est déterminé au moment de la compilation et non à celui de l'exécution par le biais des collections.  
  
 Bien que les groupes de données typés présentent de nombreux avantages, il existe diverses situations dans lesquelles un groupe de données non typé pourra s'avérer utile.  La situation la plus évidente est celle où aucun schéma n'est disponible pour le groupe de données.  Elle peut se produire, par exemple, si votre application interagit avec un composant qui retourne un groupe de données dont vous ne connaissez pas à l'avance la structure.  De même, il peut vous arriver de travailler avec des données dont la structure n'est pas prévisible et statique ; dans ce cas, il ne sera pas commode d'utiliser un groupe de données typé, parce que vous serez obligé de régénérer sa classe à chaque modification qui sera apportée à la structure des données.  
  
 Plus généralement, il arrive souvent que vous soyez amené à créer dynamiquement un groupe de données sans disposer d'un schéma.  Dans de tels cas, le groupe de données constitue simplement une structure pratique dans laquelle vous pouvez conserver des informations, à condition que les données puissent être représentées d'une manière relationnelle.  Dans le même temps, vous pouvez profiter des fonctionnalités propres aux groupes de données telles que la faculté de sérialiser les informations à passer à un autre processus ou d'écrire les données dans un fichier XML.  
  
## Respect de la casse dans les groupes de données  
 Dans un groupe de données, les noms de table et de colonne ne font pas, par défaut, la différence entre majuscules et minuscules ; autrement dit, une table appelée « Customers » peut être référencée par « customers ». Ce principe est conforme aux conventions d'attribution de noms de nombreuses bases de données, y compris le comportement par défaut de SQL Server, qui ne distinguent pas les noms des éléments de données uniquement par leur casse.  
  
> [!NOTE]
>  À la différence des groupes de données, les documents XML respectent la casse, si bien que les noms d'éléments de données définis dans les schémas la respectent eux aussi.  Par exemple, le protocole de schéma permet au schéma de définir une table appelée « Customers » et une autre appelée « customers ». Cela peut entraîner des collisions de noms lorsqu'un schéma contenant des éléments qui ne diffèrent que par leur casse est utilisé pour générer une classe DataSet.  
  
 Toutefois, le respect de la casse peut constituer un facteur d'interprétation des données contenues dans un groupe de données.  Par exemple, si vous filtrez les données d'une table d'un groupe de données, le critère de recherche peut retourner des résultats différents selon que la comparaison respecte ou non la casse.  Vous pouvez contrôler le respect de la casse pour le filtrage, la recherche et le tri en définissant la propriété <xref:System.Data.DataSet.CaseSensitive%2A> du groupe de données.  Toutes les tables d'un groupe de données héritent par défaut de la valeur de cette propriété.  \(Vous pouvez substituer cette propriété pour chaque table individuelle en définissant la propriété <xref:System.Data.DataTable.CaseSensitive%2A> de la table.\)  
  
## Tables connexes et objets DataRelation  
 S'il existe plusieurs tables dans un groupe de données, il est possible qu'elles contiennent des informations connexes.  Un groupe de données n'a pas connaissance de telles relations, quand elles existent ; pour travailler avec les données de tables connexes, vous pouvez par conséquent créer des objets <xref:System.Data.DataRelation> qui décrivent les relations unissant les différentes tables du groupe de données.  Pour plus d'informations, consultez [Comment : accéder aux enregistrements dans les DataTables connexes](../Topic/How%20to:%20Access%20Records%20in%20Related%20DataTables.md).  Les objets <xref:System.Data.DataRelation> peuvent être utilisés pour extraire par programmation des enregistrements enfants connexes pour un enregistrement parent et un enregistrement parent d'un enregistrement enfant.  Pour plus d'informations, consultez [Relations dans les groupes de données](../data-tools/relationships-in-datasets.md).  Si votre base de données contient des relations entre plusieurs tables, les outils de conception génèrent automatiquement les objets <xref:System.Data.DataRelation> à votre intention.  
  
 Considérons, par exemple, les données de clients et de commandes telles qu'elles existent dans la base de données Northwind.  La table `Customers` peut contenir les enregistrements suivants :  
  
```  
CustomerID   CompanyName               City  
ALFKI        Alfreds Futterkiste       Berlin  
ANTON        Antonio Moreno Taquerias  Mexico D.F.  
AROUT        Around the Horn           London  
```  
  
 Le groupe de données peut également contenir une autre table contenant des informations sur les commandes.  La table `Orders` contient un ID de client comme colonne de clé étrangère.  En ne sélectionnant que quelques colonnes de la table `Orders`, vous obtiendrez un résultat semblable à ceci :  
  
```  
OrderId    CustomerID    OrderDate  
10692      ALFKI         10/03/1997  
10702      ALFKI         10/13/1997  
10365      ANTON         11/27/1996  
10507      ANTON         4/15/1997  
```  
  
 Comme chaque client peut avoir passé plusieurs commandes, il existe une relation un\-à\-plusieurs entre les clients et les commandes.  Par exemple, dans le tableau ci\-dessus, le client ALFKI a passé deux commandes.  
  
 Vous pouvez faire appel à un objet <xref:System.Data.DataRelation> pour extraire des enregistrements connexes d'une table parente ou enfant.  Par exemple, lorsque vous travaillez avec l'enregistrement décrivant le client ANTON, vous pouvez obtenir la collection d'enregistrements décrivant les commandes de ce client.  Pour plus d'informations, consultez <xref:System.Data.DataRow.GetChildRows%2A>.  De la même façon, lorsque vous utilisez l'enregistrement décrivant l'OrderId 10507, vous pouvez naviguer vers le haut de l'objet de relation pour obtenir l'enregistrement de son parent, ANTON.  Pour plus d'informations, consultez <xref:System.Data.DataRow.GetParentRow%2A>.  
  
## Contraintes  
 Comme dans la plupart des bases de données, les groupes de données prennent en charge des contraintes qui leur permettent de garantir l'intégrité des données.  Les contraintes sont des règles qui s'appliquent lorsque des lignes sont insérées, mises  à jour ou supprimées dans une table.  Vous pouvez définir deux types de contraintes :  
  
-   une contrainte *unique* qui contrôle que les nouvelles valeurs d'une colonne ne sont pas dupliquées dans la table ;  
  
-   une contrainte de *clé étrangère* qui définit des règles de mise à jour des enregistrements enfants connexes lorsqu'un enregistrement d'une table principale est mis à jour ou supprimé.  Par exemple, une contrainte de clé étrangère vérifie qu'il existe un enregistrement parent avant d'autoriser la création de tout enregistrement enfant.  
  
 Dans un groupe de données, les contraintes sont associées à certaines tables \(contraintes de clé étrangère\) ou colonnes \(contrainte unique garantissant que les valeurs des colonnes ne sont pas dupliquées\).  Les contraintes sont implémentées en tant qu'objets de type <xref:System.Data.UniqueConstraint> ou <xref:System.Data.ForeignKeyConstraint>.  Ensuite, ils sont ajoutés à la collection <xref:System.Data.DataTable.Constraints%2A> d'un <xref:System.Data.DataTable>.  Une contrainte unique peut également être spécifiée en affectant simplement à la propriété <xref:System.Data.DataColumn.Unique%2A> d'un <xref:System.Data.DataColumn> la valeur `true`.  
  
 Le groupe de données proprement dit prend en charge une propriété booléenne <xref:System.Data.DataSet.EnforceConstraints%2A> qui indique si les contraintes seront appliquées ou non.  Par défaut, elle est définie sur `true`.  Toutefois, il peut être utile dans certains cas de désactiver temporairement les contraintes.  Le plus souvent, vous désactiverez les contraintes lorsque vous modifierez un enregistrement de telle sorte qu'il provoque temporairement un état non valide.  La modification accomplie \(et donc après rétablissement d'un état valide\) vous pourrez réactiver les contraintes.  
  
 Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous créez des contraintes implicitement lorsque vous définissez un groupe de données.  En ajoutant une clé primaire à un groupe de données, vous créez implicitement une contrainte unique pour la colonne de clé primaire.  Vous pouvez spécifier une contrainte unique pour d'autres colonnes en attribuant à leur propriété <xref:System.Data.DataColumn.Unique%2A> la valeur `true`.  
  
 Vous définissez des contraintes de clé étrangère en créant un objet <xref:System.Data.DataRelation> dans un groupe de données.  En plus de vous permettre d'obtenir par programmation des informations sur des enregistrements connexes, un objet <xref:System.Data.DataRelation> vous permet de définir des règles de contrainte de clé étrangère.  
  
## Propriétés étendues du groupe de données  
 Les propriétés étendues fournissent des mappages de noms en cas de conflit de noms lors du processus de génération du groupe de données à partir d'un fichier .xsd.  Lorsqu'un identificateur contenu dans le fichier .xsd est différent du nom calculé créé par le générateur de groupe de données, une propriété étendue est ajoutée au groupe de données dans l'espace de noms `msprop`.  Le tableau suivant affiche les propriétés étendues qui peuvent être générées :  
  
|Objet|Propriété étendue|  
|-----------|-----------------------|  
|<xref:System.Data.DataSet>|msprop:Generator\_UserDSName|  
||msprop:Generator\_DataSetName|  
|<xref:System.Data.DataTable>|msprop:Generator\_UserTableName|  
||msprop:Generator\_TablePropName|  
||msprop:Generator\_TableVarName|  
||msprop:Generator\_TableClassName|  
||msprop:Generator\_RowClassName|  
||msprop:Generator\_RowEvHandlerName|  
||msprop:Generator\_RowEvArgName|  
|<xref:System.Data.DataColumn>|msprop:Generator\_UserColumnName|  
||msprop:Generator\_ColumnPropNameInTable|  
||msprop:Generator\_ColumnVarNameInTable|  
||msprop:Generator\_ColumnPropNameInRow|  
  
## Voir aussi  
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Vue d'ensemble d'applications de données dans Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)