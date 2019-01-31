---
title: 'Erreur : Utilisateur pourrait pas exécuter la procédure stockée sp_enable_sql_debug | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e051cd594ee26a57fdbb7dcdc5bdad81f06cf771
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55024186"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>Erreur : L’utilisateur n’a pas pu exécuter la procédure stockée sp_enable_sql_debug

La procédure stockée sp_enable_sql_debug n'a pas pu s'exécuter sur le serveur. Cela peut être provoqué par :

- Un problème de connexion. Vous devez avoir une connexion stable au serveur.

- Un manque d'autorisations nécessaires sur le serveur. Pour déboguer sur SQL Server 2005, le compte exécutant Visual Studio et le compte utilisé pour la connexion à SQL Server doivent être membres du rôle sysadmin. Le compte utilisé pour la connexion à SQL Server est soit votre compte d'utilisateur Windows (si vous utilisez l'authentification Windows) soit un compte avec l'ID et le mot de passe d'utilisateur (si vous utilisez l'authentification SQL).

Pour plus d'informations, voir [Procédure : Définir des autorisations SQL Server pour le débogage](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Définir des autorisations SQL Server pour le débogage](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Configuration du débogage SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))