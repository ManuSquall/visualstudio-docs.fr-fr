---
title: 'Erreur : SQL peut&#39;t à détecter SSDEBUGPS | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3ca505d4f18ca52153d40e922aa5aa2682405fe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Erreur : SQL peut&#39;t à détecter SSDEBUGPS

SSDEBUGPS.dll est le composant SQL Server Debugging Host.

Cette erreur se produit lorsque vous essayez de commencer à déboguer, et indique que le fichier spécifié n'est pas présent sur l'ordinateur [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. Les causes possibles sont que soit le programme d'installation du débogage distant n'a jamais été exécuté, soit ce fichier a été supprimé.

Il existe deux manières de résoudre cette erreur : en réexécutant le programme d’installation le débogage distant et en copiant le fichier sur le [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] machine.

Pour réexécuter le programme d’installation de débogage à distance, suivez les instructions à [débogage distant](../debugger/remote-debugging.md).

Si vous repérez une copie du fichier ssdebugps.dll, vous pouvez le copier sur le [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] machine. S'il est présent, le fichier se trouvera dans le répertoire \Program Files\Common Files\Microsoft Shared\SQL Debugging. Vous pouvez le trouver sur un autre [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] ordinateur, ou sur un ordinateur équipé de Visual Studio 2005 est installé.

Pour copier SSDEBUGPS.dll sur l’ordinateur SQL Server 2005 :

1. Copiez le fichier dans le répertoire portant le même nom et chemin d’accès sur le [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] machine.

2. Inscrivez-le en ouvrant un **invite de commandes**et en exécutant la commande suivante :

    ```
    regsrv32 ssdebugps.dll
    ```