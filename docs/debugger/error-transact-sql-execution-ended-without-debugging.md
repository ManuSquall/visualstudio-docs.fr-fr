---
title: 'Erreur : L’exécution de Transact-SQL s’est terminée sans débogage | Microsoft Docs'
ms.date: 11/08/2018
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
ms.openlocfilehash: ce27a15766af51a10cf1697f3ed08e6aebf2bb96
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53863054"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Erreur : L’exécution de Transact-SQL s’est terminée sans débogage

Cette erreur se produit lorsque vous tentez de déboguer un Transact-SQL ou une procédure SQLCLR et le débogueur ne reçoit les messages de débogage à partir du serveur SQL.  
  
Ce problème peut être en raison de problèmes réseau ou des problèmes sur le serveur SQL Server, mais la cause la plus probable est un problème d’autorisation.  
  
Deux comptes sont concernés :  
  
- Le compte d'application est le compte utilisateur qu'utilise [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour s'exécuter.  
  
- Le compte de connexion est l'identité utilisée pour établir la connexion à SQL Server. Ce compte n’est pas nécessairement identique à l’identité de Visual Studio s’exécute comme si la connexion à l’aide de l’authentification SQL.  
  
  Le débogage SQL requiert que le compte d’application doit correspondre au compte de connexion ou être un administrateur système.  
  
  Si vous utilisez un nom de compte SQL comme sa, le compte de l’application doit être configuré sur le serveur SQL Server en tant qu’administrateur système. Par défaut, les administrateurs sur l’ordinateur SQL server est en cours d’exécution sont des administrateurs système SQL Server.  
  
  Pour corriger cette erreur, vous pouvez avoir besoin de :  
  
  - Vérifier vos paramètres d'autorisation. Pour plus d'informations, voir [Procédure : Définir des autorisations SQL Server pour le débogage](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
  - Vérifier que le débogage SQL est correctement configuré.  
  
  - Consulter votre administrateur réseau ou de base de données.  
  
## <a name="see-also"></a>Voir aussi

- [Configuration du débogage SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Guide pratique pour Définir des autorisations SQL Server pour le débogage](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)
- [Remote Debugging](../debugger/remote-debugging.md)