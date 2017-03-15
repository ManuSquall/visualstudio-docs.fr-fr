---
title: "D&#233;pannage des exceptions&#160;: System.Data.OracleClient.OracleException | Microsoft Docs"
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
  - "OracleException (classe)"
  - "Oracle"
  - "exceptions, Oracle"
ms.assetid: 08b9206e-baa9-4caa-b0c7-ece2118f6e2d
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.Data.OracleClient.OracleException
Une exception <xref:System.Data.OracleClient.OracleException> est générée lorsqu'un avertissement ou une erreur est retourné par une base de données Oracle ou le fournisseur de données .NET Framework pour Oracle.  
  
## Conseils associés  
 **Vérifiez que vous vous connectez à l'aide d'informations d'identification valides.**  
 Assurez\-vous que les informations d'identification que vous fournissez sont valides.  
  
 **Vérifiez que le nom de serveur est correct et que le serveur s'exécute.**  
 Assurez\-vous que vous utilisez le nom de serveur correct et que le serveur peut être atteint.  
  
## Remarques  
 Cette exception est levée toutes les fois que <xref:System.Data.OracleClient.OracleDataAdapter> rencontre une erreur générée par le serveur.  
  
 Si la gravité de l'erreur est trop élevée, le serveur peut fermer <xref:System.Data.OracleClient.OracleConnection>. L'utilisateur peut toutefois rouvrir la connexion et continuer.  
  
## Voir aussi  
 <xref:System.Data.OracleClient.OracleException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)