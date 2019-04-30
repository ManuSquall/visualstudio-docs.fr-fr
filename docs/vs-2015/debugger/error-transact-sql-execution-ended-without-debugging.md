---
title: 'Erreur : L’exécution de Transact-SQL s’est terminée sans débogage | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 7a4d4999-3973-4339-ba6a-f0d19bcb1d4a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 910b84e7a024547208ea2e7ae1d6a6897cf60893
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62431886"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Erreur : L’exécution de Transact-SQL s’est terminée sans débogage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette erreur se produit lorsque vous essayez de déboguer une procédure Transact-SQL ou SQLCLR et que le débogueur ne reçoit pas de messages de débogage de SQL Server.  
  
 Cela peut être dû à des problèmes liés au réseau ou à SQL Server, mais plus probablement à un problème d'autorisation.  
  
 Deux comptes sont concernés :  
  
- Le compte d'application est le compte utilisateur qu'utilise [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour s'exécuter.  
  
- Le compte de connexion est l'identité utilisée pour établir la connexion à SQL Server. Il ne s'agit pas nécessairement du compte sous lequel Visual Studio est exécuté si la connexion utilise l'authentification SQL.  
  
  Le débogage SQL requiert que le compte d'application corresponde au compte de connexion ou soit administrateur système.  
  
  Si vous utilisez un nom d'utilisateur SQL comme sa, le compte d'application doit être configuré sur le SQL Server comme un administrateur système. Par défaut, les administrateurs de l'ordinateur sur lequel SQL Server est exécuté sont des administrateurs système SQL Server.  
  
  Pour corriger cette erreur, vous pouvez avoir besoin de :  
  
- Vérifier vos paramètres d'autorisation. Pour plus d'informations, voir [Procédure : Définir des autorisations SQL Server pour le débogage](http://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
- Vérifier que le débogage SQL est correctement configuré.  
  
- Consulter votre administrateur réseau ou de base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration du débogage SQL](http://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [Guide pratique pour Définir des autorisations SQL Server pour le débogage](http://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
