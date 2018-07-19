---
title: 'Erreur : SQL peut&#39;t à détecter SSDEBUGPS | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
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
ms.openlocfilehash: 1498a287bdb474751dfaa5b4b23c30bc302544e7
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058254"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Erreur : SQL peut&#39;t à détecter SSDEBUGPS

SSDEBUGPS.dll est le composant SQL Server Debugging Host.

Cette erreur se produit lorsque vous essayez de commencer à déboguer, et indique que le fichier spécifié n'est pas présent sur l'ordinateur [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. Les causes possibles sont que soit le programme d'installation du débogage distant n'a jamais été exécuté, soit ce fichier a été supprimé.

Il existe deux façons pour résoudre cette erreur : en réexécutant le programme d’installation le débogage distant et en copiant le fichier sur le [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] machine.

Pour réexécuter le programme d’installation le débogage à distance, suivez les instructions de [le débogage à distance](../debugger/remote-debugging.md).

Si vous repérez une copie du fichier ssdebugps.dll, vous pouvez le copier sur le [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] machine. S'il est présent, le fichier se trouvera dans le répertoire \Program Files\Common Files\Microsoft Shared\SQL Debugging. Vous pouvez le trouver sur un autre [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] machine, ou sur un ordinateur équipé de Visual Studio 2005 est installé.

Pour copier SSDEBUGPS.dll sur l’ordinateur SQL Server 2005 :

1. Copiez le fichier dans le répertoire portant le même nom et chemin d’accès sur le [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] machine.

2. Inscrivez-le en ouvrant un **invite de commandes**et en exécutant la commande suivante :

    ```cmd
    regsrv32 ssdebugps.dll
    ```
