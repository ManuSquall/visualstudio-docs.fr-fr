---
title: "Erreur : ASP.NET ne pas installé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.http_not_supported
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aec590a018e102e6ab3dd8d2607d9720991e9f90
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="error-aspnet-not-installed"></a>Erreur : ASP.NET n'est pas installé
Cette erreur se produit quand [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] n'est pas installé correctement sur l'ordinateur que vous tentez de déboguer. Cela peut signifier qu'[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] n'a jamais été installé ou qu'[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] a été installé avant les services IIS (Internet Information Services).  
  
### <a name="to-reinstall-aspnet"></a>Pour réinstaller ASP.NET  
  
1.  À partir d'une invite de commandes, exécutez la commande suivante :  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     où *version* représente le numéro de version du .NET Framework installée sur votre ordinateur, comme v1.0.370. Vous pouvez déterminer la version de framework en consultant le `\WINDOWS\Microsoft.NET\Framework` active.  
  
    > [!NOTE]
    >  Avec Windows Server 2003, vous pouvez installer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] à l’aide de **Ajout / Suppression de programmes** dans le panneau de configuration.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’applications web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)