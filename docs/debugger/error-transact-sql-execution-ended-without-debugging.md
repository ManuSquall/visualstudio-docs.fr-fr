---
title: 'Erreur : l’exécution de Transact-SQL s’est terminée sans débogage | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e86e24f775d8470b54ed7b9c54d27a5d3c1ee8da
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916301"
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

  - Vérifier vos paramètres d'autorisation. Pour plus d’informations, consultez [Comment : définir des autorisations de SQL Server pour le débogage](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

  - Vérifier que le débogage SQL est correctement configuré.

  - Consulter votre administrateur réseau ou de base de données.

## <a name="see-also"></a>Voir aussi

- [Configuration du débogage SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Comment : définir des autorisations de SQL Server pour le débogage](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)
- [Remote Debugging](../debugger/remote-debugging.md)