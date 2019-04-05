---
title: 'Erreur : Utilisateur pourrait pas exécuter la procédure stockée sp_enable_sql_debug | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_accessdenied
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 11957495-c238-4cc5-8937-e4026f5e10e1
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1f463aca03cd0e869f4028f8e086c623295fd2f6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953603"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>Erreur : L’utilisateur n’a pas pu exécuter la procédure stockée sp_enable_sql_debug
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La procédure stockée sp_enable_sql_debug n'a pas pu s'exécuter sur le serveur. Cela peut être provoqué par :  
  
- Un problème de connexion. Vous devez avoir une connexion stable au serveur.  
  
- Un manque d'autorisations nécessaires sur le serveur. Pour déboguer sur SQL Server 2005, le compte exécutant Visual Studio et le compte utilisé pour la connexion à SQL Server doivent être membres du rôle sysadmin. Le compte utilisé pour la connexion à SQL Server est soit votre compte d'utilisateur Windows (si vous utilisez l'authentification Windows) soit un compte avec l'ID et le mot de passe d'utilisateur (si vous utilisez l'authentification SQL).  
  
  Pour plus d'informations, voir [Procédure : Définir des autorisations SQL Server pour le débogage](http://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Définir des autorisations SQL Server pour le débogage](http://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Configuration du débogage SQL](http://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3)
