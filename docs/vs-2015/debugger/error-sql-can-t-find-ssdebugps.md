---
title: 'Erreur : SQL peut&#39;t Rechercher SSDEBUGPS | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 25462a99bd3e773f03af3918a9e25d11ed006c1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185215"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Erreur : SQL peut&#39;t Rechercher SSDEBUGPS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SSDEBUGPS.dll est le composant SQL Server Debugging Host.  
  
 Cette erreur se produit lorsque vous essayez de commencer à déboguer, et indique que le fichier spécifié n'est pas présent sur l'ordinateur [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]. Les causes possibles sont que soit le programme d'installation du débogage distant n'a jamais été exécuté, soit ce fichier a été supprimé.  
  
 Il existe deux manières de résoudre cette erreur : en réexécutant le programme d’installation du débogage distant et en copiant le fichier sur l’ordinateur [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)].  
  
 Pour réexécuter le programme d’installation du débogage distant, suivez les instructions dans [débogage distant](../debugger/remote-debugging.md).  
  
 Si vous trouvez une copie du fichier ssdebugps.dll, vous pouvez le copier sur l’ordinateur [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]. S'il est présent, le fichier se trouvera dans le répertoire \Program Files\Common Files\Microsoft Shared\SQL Debugging. Vous pouvez le trouver sur un autre [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] ordinateur ou sur un ordinateur sur lequel est [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] installé.  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>Pour copier SSDEBUGPS.dll sur l'ordinateur SQL Server 2005  
  
1. Copiez le fichier dans le répertoire avec le même nom et chemin d’accès sur l’ordinateur [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)].  
  
2. Inscrivez-le en ouvrant une **Invite de commande**, et en exécutant la commande suivante :  
  
    ```  
    regsvr32 ssdebugps.dll  
    ```
