---
title: 'Erreur : SQL peut&#39;t à détecter SSDEBUGPS | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 47e0557e3ad2022250d54b7bd45844825ff79a03
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757466"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Erreur : SQL peut&#39;t à détecter SSDEBUGPS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SSDEBUGPS.dll est le composant SQL Server Debugging Host.  
  
 Cette erreur se produit lorsque vous essayez de commencer à déboguer, et indique que le fichier spécifié n'est pas présent sur l'ordinateur [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]. Les causes possibles sont que soit le programme d'installation du débogage distant n'a jamais été exécuté, soit ce fichier a été supprimé.  
  
 Il existe deux façons pour résoudre cette erreur : en réexécutant le programme d’installation le débogage distant et en copiant le fichier sur le [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] machine.  
  
 Pour réexécuter le programme d’installation le débogage à distance, suivez les instructions de [le débogage à distance](../debugger/remote-debugging.md).  
  
 Si vous repérez une copie du fichier ssdebugps.dll, vous pouvez le copier sur le [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] machine. S'il est présent, le fichier se trouvera dans le répertoire \Program Files\Common Files\Microsoft Shared\SQL Debugging. Vous pouvez le trouver sur un autre [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] machine, ou sur un ordinateur qui a [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] installé.  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>Pour copier SSDEBUGPS.dll sur l'ordinateur SQL Server 2005  
  
1.  Copiez le fichier dans le répertoire portant le même nom et chemin d’accès sur le [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] machine.  
  
2.  Inscrivez-le en ouvrant un **invite de commandes**et en exécutant la commande suivante :  
  
    ```  
    regsrv32 ssdebugps.dll  
    ```



