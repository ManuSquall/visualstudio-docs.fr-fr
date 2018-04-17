---
title: 'Erreur : L’exécution de Transact-SQL s’est terminée sans débogage | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 621d6411a6702b4449768ee6850e5bdf42b85946
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Erreur : L'exécution de Transact-SQL s'est terminée sans débogage
Cette erreur se produit lorsque vous essayez de déboguer une procédure Transact-SQL ou SQLCLR et que le débogueur ne reçoit pas de messages de débogage de SQL Server.  
  
 Cela peut être dû à des problèmes liés au réseau ou à SQL Server, mais plus probablement à un problème d'autorisation.  
  
 Deux comptes sont concernés :  
  
-   Le compte d'application est le compte utilisateur qu'utilise [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour s'exécuter.  
  
-   Le compte de connexion est l'identité utilisée pour établir la connexion à SQL Server. Il ne s'agit pas nécessairement du compte sous lequel Visual Studio est exécuté si la connexion utilise l'authentification SQL.  
  
 Le débogage SQL requiert que le compte d'application corresponde au compte de connexion ou soit administrateur système.  
  
 Si vous utilisez un nom d'utilisateur SQL comme sa, le compte d'application doit être configuré sur le SQL Server comme un administrateur système. Par défaut, les administrateurs de l'ordinateur sur lequel SQL Server est exécuté sont des administrateurs système SQL Server.  
  
 Pour corriger cette erreur, vous pouvez avoir besoin de :  
  
-   Vérifier vos paramètres d'autorisation. Pour plus d’informations, consultez [Comment : définir des autorisations SQL Server pour le débogage](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
-   Vérifier que le débogage SQL est correctement configuré.  
  
-   Consulter votre administrateur réseau ou de base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de débogage SQL](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [Comment : définir des autorisations SQL Server pour le débogage](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)   
 [Débogage à distance](../debugger/remote-debugging.md)