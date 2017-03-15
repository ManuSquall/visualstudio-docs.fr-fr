---
title: "Comment&#160;: mettre &#224; jour les donn&#233;es &#224; l&#39;aide d&#39;un TableAdapter | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "données (Visual Studio), enregistrer"
  - "données (Visual Studio), TableAdapters"
  - "données (Visual Studio), mettre à jour"
  - "enregistrer les données"
  - "TableAdapters, mise à jour de données"
  - "mise à jour de données, TableAdapters"
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comment&#160;: mettre &#224; jour les donn&#233;es &#224; l&#39;aide d&#39;un TableAdapter
Lorsque les données contenues dans votre groupe de données ont été modifiées et validées, vous souhaiterez probablement renvoyer les données mises à jour vers une base de données.  Pour envoyer les données modifiées à une base de données, vous appelez la méthode `Update` d'un [TableAdapter](../data-tools/tableadapter-overview.md).  La méthode `Update` de l'adaptateur met à jour une table de données unique et exécute la commande correcte \(INSERT, UPDATE ou DELETE\) en fonction du <xref:System.Data.DataRow.RowState%2A> de chaque ligne de données contenue dans la table.  Lorsque vous enregistrez des données dans des tables connexes, Visual Studio fournit un composant TableAdapterManager qui aide à effectuer des enregistrements dans l'ordre approprié selon les contraintes de clé étrangère définies dans la base de données.  Pour plus d'informations, consultez [Vue d'ensemble de la mise à jour hiérarchique](../Topic/Hierarchical%20Update%20Overview.md).  
  
> [!NOTE]
>  Étant donné que la tentative de mise à jour d'une source de données avec le contenu d'un groupe de données peut entraîner des erreurs, il est conseillé de placer le code qui appelle la méthode `Update` de l'adaptateur dans un bloc `try`\/`catch`.  
  
 La procédure exacte de mise à jour d'une source de données varie en fonction des besoins de votre entreprise, mais votre application doit comprendre les étapes suivantes :  
  
1.  Appelez la méthode `Update` de l'adaptateur dans un bloc `try`\/`catch`.  
  
2.  Si une exception est interceptée, rechercher la ligne de données ayant provoqué l'erreur.  Pour plus d'informations, consultez [Comment : trouver des lignes contenant des erreurs](../Topic/How%20to:%20Locate%20Rows%20that%20Have%20Errors.md).  
  
3.  Résolvez le problème dans la ligne de données \(par programmation si possible ou en affichant la ligne non valide pour que l'utilisateur la modifie\), puis retentez la mise à jour \(<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>\).  
  
## Enregistrement des données dans une base de données  
 Appelez la méthode `Update` d'un TableAdapter en passant le nom de la table de données contenant les valeurs à écrire dans la base de données.  
  
#### Pour mettre à jour une base de données avec un groupe de données à l'aide d'un TableAdapter  
  
-   Insérez la méthode `Update` de l'adaptateur dans un bloc `try`\/`catch`.  L'exemple suivant illustre une tentative de mise à jour depuis un bloc `try`\/`catch` avec le contenu de la table `Customers` dans `NorthwindDataSet`.  
  
     [!code-cs[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]  
  
## Mise à jour de deux tables connexes dans un groupe de données avec un TableAdapter  
 Lors de la mise à jour de tables connexes dans un groupe de données, il est important de respecter l'ordre afin de réduire les risques de non respect des contraintes d'intégrité référentielle.  L'ordre d'exécution des commandes respectera également les indices du <xref:System.Data.DataRowCollection> contenu dans le groupe de données.  Pour éviter le déclenchement d'erreurs d'intégrité des données, il est recommandé de mettre à jour la base de données en respectant la séquence suivante :  
  
1.  Table enfant : suppression des enregistrements.  
  
2.  Table parente : insertion, mise à jour et suppression des enregistrements.  
  
3.  Table enfant : insertion et mise à jour des enregistrements.  
  
    > [!NOTE]
    >  Si vous mettez à jour plusieurs tables connexes, vous devez inclure toute la logique de mise à jour dans une transaction.  Une transaction est un processus qui garantit que toutes les modifications connexes apportées à une base de données sont appliquées avec succès avant de valider toute modification.  Pour plus d'informations, consultez [Transactions et concurrence](../Topic/Transactions%20and%20Concurrency.md).  
  
#### Pour mettre à jour deux tables connexes à l'aide d'un TableAdapter  
  
1.  Créez trois tables de données temporaires qui contiendront les différents enregistrements.  
  
2.  Appelez la méthode `Update` pour chaque sous\-ensemble de lignes à partir d'un bloc `try`\/`catch`.  Si des erreurs de mise à jour se produisent, vous devez vous débrancher et les résoudre.  
  
3.  Validez les modifications apportées à la base de données.  
  
4.  Éliminez les tables de données temporaires pour libérer les ressources.  
  
     L'exemple suivant montre comment mettre à jour une source de données à l'aide d'un groupe de données contenant des tables connexes.  
  
     [!code-vb[VbRaddataSaving#27](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_2.vb)]
     [!code-cs[VbRaddataSaving#27](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_2.cs)]  
  
## Voir aussi  
 [Vue d'ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Procédures pas à pas relatives aux données](../Topic/Data%20Walkthroughs.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)