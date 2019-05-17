---
title: 'CA2100 : Vérifier si les requêtes SQL présentent des failles de sécurité'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5387ce65532cb532192191bd67f29cc7af6e28c0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545291"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100 : Vérifier si les requêtes SQL présentent des failles de sécurité

|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode définit le <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> propriété à l’aide d’une chaîne qui est construite à partir d’un argument de chaîne à la méthode.

## <a name="rule-description"></a>Description de la règle

Cette règle suppose que l’argument de chaîne contient des entrées d’utilisateur. Une chaîne de commande SQL générée par une entrée d'utilisateur est vulnérable aux attaques par injection de code SQL. Dans une attaque par injection SQL, un utilisateur malveillant fournit des entrées qui modifie la conception d’une requête dans le but d’endommager ou d’accès non autorisé à la base de données sous-jacente. Les techniques classiques englobent l’injection d’un guillemet ou une apostrophe, qui est le délimiteur de chaîne littérale SQL ; deux tirets, ce qui signifie un commentaire SQL ; et un point-virgule, ce qui indique qu’une nouvelle commande suit. Si l’entrée d’utilisateur doit faire partie de la requête, utilisez un des éléments suivants, répertoriés par ordre d’efficacité, afin de réduire le risque d’attaque.

- Utiliser une procédure stockée.

- Utilisez une chaîne de commande paramétrable.

- Valider l’entrée d’utilisateur pour le type et le contenu avant de générer la chaîne de commande.

Les types .NET Framework suivantes implémentent la <xref:System.Data.IDbCommand.CommandText%2A> propriété ou fournissent des constructeurs qui définissent la propriété à l’aide d’un argument de chaîne.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> et <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> et <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> et <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> et <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

Notez que cette règle est violée lorsque la méthode ToString d’un type est utilisée explicitement ou implicitement pour construire la chaîne de requête. Voici un exemple.

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 La règle est enfreinte, car un utilisateur malveillant peut substituer la méthode ToString().

 La règle est enfreinte lors de la méthode ToString est utilisée implicitement.

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, utilisez une requête paramétrable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si le texte de commande ne contient pas d’entrée d’utilisateur.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode, `UnsafeQuery`, qui enfreint la règle et une méthode, `SaferQuery`, qui satisfait la règle en utilisant une chaîne de commande paramétrable.

 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]

## <a name="see-also"></a>Voir aussi
 [Vue d’ensemble de la sécurité](/dotnet/framework/data/adonet/security-overview)