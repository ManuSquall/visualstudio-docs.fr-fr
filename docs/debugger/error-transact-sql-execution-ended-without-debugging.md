---
title: 'Erreur : L’exécution de Transact-SQL s’est terminée sans débogage | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
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
ms.openlocfilehash: 1bc4de5e9ef0830f69b60d773a59411c4b691454
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894753"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Erreur : L'exécution de Transact-SQL s'est terminée sans débogage
Cette erreur se produit lorsque vous essayez de déboguer une procédure Transact-SQL ou SQLCLR et que le débogueur ne reçoit pas de messages de débogage de SQL Server.  
  
 Cela peut être dû à des problèmes liés au réseau ou à SQL Server, mais plus probablement à un problème d'autorisation.  
  
 Deux comptes sont concernés :  
  
- Le compte d'application est le compte utilisateur qu'utilise [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour s'exécuter.  
  
- Le compte de connexion est l'identité utilisée pour établir la connexion à SQL Server. Il ne s'agit pas nécessairement du compte sous lequel Visual Studio est exécuté si la connexion utilise l'authentification SQL.  
  
  Le débogage SQL requiert que le compte d'application corresponde au compte de connexion ou soit administrateur système.  
  
  Si vous utilisez un nom d'utilisateur SQL comme sa, le compte d'application doit être configuré sur le SQL Server comme un administrateur système. Par défaut, les administrateurs de l'ordinateur sur lequel SQL Server est exécuté sont des administrateurs système SQL Server.  
  
  Pour corriger cette erreur, vous pouvez avoir besoin de :  
  
- Vérifier vos paramètres d'autorisation. Pour plus d’informations, consultez [Comment : définir des autorisations SQL Server pour le débogage](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
- Vérifier que le débogage SQL est correctement configuré.  
  
- Consulter votre administrateur réseau ou de base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration du débogage SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))   
 [Comment : définir des autorisations SQL Server pour le débogage](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)   
 [Remote Debugging](../debugger/remote-debugging.md)