---
title: "D&#233;pannage des exceptions&#160;: System.Data.SqlClient.SqlException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "SqlException (classe)"
ms.assetid: 05f63457-3825-4541-ae09-0c771eb5ba35
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.Data.SqlClient.SqlException
Une exception <xref:System.Data.SqlClient.SqlException> est générée lorsqu'un avertissement ou une erreur est retourné par SQL Server.  
  
## Conseils associés  
 **Vérifiez que vous vous connectez à l'aide d'informations d'identification valides.**  
 Assurez\-vous que les informations d'identification que vous fournissez sont valides. Pour plus d'informations, consultez [How to: Access SQL Server Using Predetermined Credentials](../Topic/How%20to:%20Access%20SQL%20Server%20Using%20Predetermined%20Credentials.md).  
  
 **Vérifiez que le nom de serveur est correct et que le serveur s'exécute.**  
 Assurez\-vous que vous utilisez le nom de serveur correct et que le serveur peut être atteint.  
  
### Notes  
 Cette exception est levée toutes les fois où le fournisseur de données .NET Framework pour SQL Server rencontre une erreur générée par le serveur.  
  
 Les messages dont le niveau de gravité est inférieur ou égal à 10 correspondent à des messages d'information qui indiquent des problèmes dus à des erreurs dans des informations entrées par un utilisateur. Les niveaux de gravité compris entre 11 et 16 désignent des erreurs générées par l'utilisateur et pouvant être corrigées par celui\-ci. Les niveaux de gravité compris entre 17 et 25 indiquent des erreurs logicielles ou matérielles. Lorsqu'une erreur de niveau 17, 18 ou 19 se produit, vous pouvez continuer à travailler, mais vous ne pouvez peut\-être pas exécuter une instruction particulière.  
  
 <xref:System.Data.SqlClient.SqlConnection> reste ouvert lorsque le niveau de gravité est inférieur ou égal à 19. Lorsque le niveau de gravité est supérieur ou égal à 20, le serveur ferme généralement <xref:System.Data.SqlClient.SqlConnection>. L'utilisateur peut toutefois rouvrir la connexion et continuer. Dans les deux cas, <xref:System.Data.SqlClient.SqlException> est généré par la méthode qui exécute la commande.  
  
 Pour obtenir des informations sur les messages d'avertissement et d'information envoyés par SQL Server, consultez la section Dépannage de la documentation en ligne de SQL Server.  
  
## Voir aussi  
 <xref:System.Data.SqlClient.SqlException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [How to: Access SQL Server Using Predetermined Credentials](../Topic/How%20to:%20Access%20SQL%20Server%20Using%20Predetermined%20Credentials.md)