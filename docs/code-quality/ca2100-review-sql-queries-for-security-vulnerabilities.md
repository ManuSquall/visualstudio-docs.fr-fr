---
title: "CA2100 : Rechercher des failles de s&#233;curit&#233; dans des requ&#234;tes&#160;SQL | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Review SQL queries for security vulnerabilities"
  - "ReviewSqlQueriesForSecurityVulnerabilities"
  - "CA2100"
helpviewer_keywords: 
  - "CA2100"
  - "ReviewSqlQueriesForSecurityVulnerabilities"
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2100 : Rechercher des failles de s&#233;curit&#233; dans des requ&#234;tes&#160;SQL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|  
|CheckId|CA2100|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une méthode définit la propriété <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> en utilisant une chaîne construite à partir d'un argument de chaîne de la méthode.  
  
## Description de la règle  
 Cette règle suppose que l'argument de chaîne contient des entrées d'utilisateur.  Une chaîne de commande SQL générée par une entrée d'utilisateur est vulnérable aux attaques par injection de code SQL.  Dans une attaque d'injection SQL, un utilisateur malveillant fournit des entrées qui modifient le design d'une requête afin d'endommager ou de bénéficier d'un accès non autorisé à la base de données sous\-jacente.  Les techniques classiques englobent l'injection d'un guillemet simple ou d'une apostrophe qui est le séparateur de chaîne littérale SQL ; de deux tirets qui signifient un commentaire SQL ; et d'un point\-virgule qui indique qu'une nouvelle commande suit.  Si les entrées d'utilisateur doivent faire partie de la requête, utilisez l'une des méthodes suivantes, répertoriées par ordre d'efficacité, pour réduire le risque d'attaque.  
  
-   Utilisez une procédure stockée.  
  
-   Utilisez une chaîne de commande paramétrée.  
  
-   Validez les entrées d'utilisateur pour le type et le contenu avant de générer la chaîne de commande.  
  
 Les types suivants du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] implémentent la propriété <xref:System.Data.IDbCommand.CommandText%2A> ou fournissent des constructeurs qui définissent la propriété à l'aide d'un argument de chaîne.  
  
-   <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> et <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> et <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> et <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>  
  
-   [System.Data.SqlServerCe.SqlCeCommand](assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&autoUpgrade=True) et [System.Data.SqlServerCe.SqlCeDataAdapter](assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&autoUpgrade=True)  
  
-   <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> et <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>  
  
 Notez que cette règle n'est pas respectée lorsque la méthode ToString d'un type est utilisée explicitement ou implicitement pour construire la chaîne de requête.  Voici un exemple :  
  
```  
int x = 10;  
string query = "SELECT TOP " + x.ToString() + " FROM Table";  
```  
  
 La règle n'est pas respectée car un utilisateur malveillant peut substituer la méthode ToString\(\).  
  
 La règle n'est pas respectée également lorsque la méthode ToString est utilisée implicitement.  
  
```  
int x = 10;  
string query = String.Format("SELECT TOP {0} FROM Table", x);  
```  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, utilisez une requête paramétrée.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si le texte de commande ne contient pas d'entrée d'utilisateur.  
  
## Exemple  
 L'exemple suivant présente une méthode, `UnsafeQuery`, qui viole la règle et une méthode, `SaferQuery`, qui satisfait à la règle en utilisant une chaîne de commande paramétrée.  
  
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
 [!code-cs[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]  
  
## Voir aussi  
 [Vue d'ensemble de la sécurité](../Topic/Security%20Overview2.md)