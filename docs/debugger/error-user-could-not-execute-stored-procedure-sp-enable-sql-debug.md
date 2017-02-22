---
title: "Erreur&#160;: L&#39;utilisateur n&#39;a pas pu ex&#233;cuter la proc&#233;dure stock&#233;e sp_enable_sql_debug | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.sqlde_accessdenied"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 11957495-c238-4cc5-8937-e4026f5e10e1
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Erreur&#160;: L&#39;utilisateur n&#39;a pas pu ex&#233;cuter la proc&#233;dure stock&#233;e sp_enable_sql_debug
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La procédure stockée sp\_enable\_sql\_debug n'a pas pu s'exécuter sur le serveur.  Cela peut être provoqué par :  
  
-   Un problème de connexion.  Vous devez avoir une connexion stable au serveur.  
  
-   Un manque d'autorisations nécessaires sur le serveur.  Pour déboguer sur SQL Server 2005, le compte exécutant Visual Studio et le compte utilisé pour la connexion à SQL Server doivent être membres du rôle sysadmin.  Le compte utilisé pour la connexion à SQL Server est soit votre compte d'utilisateur Windows \(si vous utilisez l'authentification Windows\) soit un compte avec l'ID et le mot de passe d'utilisateur \(si vous utilisez l'authentification SQL\).  
  
 Pour plus d'informations, consultez [How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/fr-fr/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
## Voir aussi  
 [How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/fr-fr/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Setting Up SQL Debugging](http://msdn.microsoft.com/fr-fr/3db09e68-edcc-42de-9c22-4e97cfd55ab3)