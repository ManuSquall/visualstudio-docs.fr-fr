---
title: "Erreur : SQL peut &#39; t rechercher pas SSDEBUGPS | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43a437cfc4be1c9168b16e4b9d1a46e2eadcb2e6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Erreur : SQL peut &#39; t rechercher pas SSDEBUGPS
SSDEBUGPS.dll est le composant SQL Server Debugging Host.  
  
 Cette erreur se produit lorsque vous essayez de commencer à déboguer, et indique que le fichier spécifié n'est pas présent sur l'ordinateur [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. Les causes possibles sont que soit le programme d'installation du débogage distant n'a jamais été exécuté, soit ce fichier a été supprimé.  
  
 Il existe deux manières de résoudre cette erreur : en réexécutant le programme d’installation le débogage distant et en copiant le fichier sur le [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] machine.  
  
 Pour réexécuter le programme d’installation de débogage à distance, suivez les instructions à [débogage distant](../debugger/remote-debugging.md).  
  
 Si vous repérez une copie du fichier ssdebugps.dll, vous pouvez le copier sur le [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] machine. S'il est présent, le fichier se trouvera dans le répertoire \Program Files\Common Files\Microsoft Shared\SQL Debugging. Vous pouvez le trouver sur un autre [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] ordinateur, ou sur un ordinateur qui a [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] installé.  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>Pour copier SSDEBUGPS.dll sur l'ordinateur SQL Server 2005  
  
1.  Copiez le fichier dans le répertoire portant le même nom et chemin d’accès sur le [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] machine.  
  
2.  Inscrivez-le en ouvrant un **invite de commandes**et en exécutant la commande suivante :  
  
    ```  
    regsrv32 ssdebugps.dll  
    ```