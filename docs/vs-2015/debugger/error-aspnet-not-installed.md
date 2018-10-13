---
title: 'Erreur : ASP.NET ne pas installé | Microsoft Docs'
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
- vs.debug.error.http_not_supported
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35268c6867c5438f2f3d0c4c4f9e649451a21991
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220972"
---
# <a name="error-aspnet-not-installed"></a>Erreur : ASP.NET n'est pas installé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette erreur se produit quand [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] n'est pas installé correctement sur l'ordinateur que vous tentez de déboguer. Cela peut signifier qu'[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] n'a jamais été installé ou qu'[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] a été installé avant les services IIS (Internet Information Services).  
  
### <a name="to-reinstall-aspnet"></a>Pour réinstaller ASP.NET  
  
1.  À partir d'une invite de commandes, exécutez la commande suivante :  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     où *version* représente le numéro de version du .NET Framework installée sur votre ordinateur, par exemple v1.0.370. Vous pouvez déterminer la version du framework en consultant le `\WINDOWS\Microsoft.NET\Framework` directory.  
  
    > [!NOTE]
    >  Avec Windows Server 2003, vous pouvez installer [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] à l’aide de **Ajout / Suppression de programmes** dans le panneau de configuration.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’applications web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



