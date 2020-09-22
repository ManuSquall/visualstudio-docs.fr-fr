---
title: L’exécution de Transact-SQL s’est terminée sans débogage | Microsoft Docs
ms.date: 11/08/2018
ms.topic: error-reference
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66a1f60673d1bdfb58b1a101bd1571637c41f556
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851526"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Erreur : L'exécution de Transact-SQL s'est terminée sans débogage

Cette erreur se produit lorsque vous essayez de déboguer une procédure Transact-SQL ou SQLCLR et que le débogueur ne reçoit pas de messages de débogage de la SQL Server.

Ce problème peut être dû à des problèmes de réseau ou à des problèmes sur le SQL Server, mais la cause la plus probable est un problème d’autorisations.

Deux comptes sont concernés :

- Le compte d'application est le compte utilisateur qu'utilise [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour s'exécuter.

- Le compte de connexion est l'identité utilisée pour établir la connexion à SQL Server. Ce compte n’est pas nécessairement identique à l’identité utilisée par Visual Studio si la connexion utilise l’authentification SQL.

  Le débogage SQL requiert que le compte d’application corresponde au compte de connexion ou à un administrateur système.

  Si vous utilisez un nom de compte SQL comme sa, le compte d’application doit être configuré sur le SQL Server en tant que sysadmin. Par défaut, les administrateurs sur l’ordinateur sur lequel SQL Server est en cours d’exécution sont SQL Server sysadmins.

  Pour corriger cette erreur, vous pouvez avoir besoin de :

  - Vérifier vos paramètres d'autorisation. Pour plus d’informations, consultez [Comment : définir des autorisations de SQL Server pour le débogage](/previous-versions/w1bhybwz(v=vs.100)).

  - Vérifier que le débogage SQL est correctement configuré.

  - Consulter votre administrateur réseau ou de base de données.

## <a name="see-also"></a>Voir aussi

- [Configuration du débogage SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Comment : définir des autorisations de SQL Server pour le débogage](/previous-versions/w1bhybwz(v=vs.100))
- [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)
- [Débogage à distance](../debugger/remote-debugging.md)