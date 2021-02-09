---
title: SQL peut &apos; Rechercher SSDEBUGPS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 67d7602357a39cbdce0c96b494f4c02758533e73
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871388"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Erreur : SQL peut&#39;t Rechercher SSDEBUGPS

SSDEBUGPS.dll est le composant SQL Server Debugging Host.

Cette erreur se produit lorsque vous essayez de commencer à déboguer, et indique que le fichier spécifié n'est pas présent sur l'ordinateur [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. Les causes possibles sont que soit le programme d'installation du débogage distant n'a jamais été exécuté, soit ce fichier a été supprimé.

Il existe deux manières de résoudre cette erreur : en réexécutant le programme d’installation du débogage distant et en copiant le fichier sur l’ordinateur [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].

Pour réexécuter le programme d’installation du débogage distant, suivez les instructions dans [débogage distant](../debugger/remote-debugging.md).

Si vous trouvez une copie du fichier ssdebugps.dll, vous pouvez le copier sur l’ordinateur [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. S'il est présent, le fichier se trouvera dans le répertoire \Program Files\Common Files\Microsoft Shared\SQL Debugging. Vous pouvez le trouver sur un autre [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] ordinateur ou sur un ordinateur sur lequel Visual Studio 2005 est installé.

Pour copier SSDEBUGPS.dll sur l’ordinateur SQL Server 2005 :

1. Copiez le fichier dans le répertoire avec le même nom et chemin d’accès sur l’ordinateur [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].

2. Inscrivez-le en ouvrant une **Invite de commande**, et en exécutant la commande suivante :

    ```cmd
    regsvr32 ssdebugps.dll
    ```
