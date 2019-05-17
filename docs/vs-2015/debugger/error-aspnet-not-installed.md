---
title: 'Erreur : ASP.NET n’est ne pas installé | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2198ed401f714353be2dd18846dd527cc433e695
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447313"
---
# <a name="error-aspnet-not-installed"></a>Erreur : ASP.NET n’est pas installé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette erreur se produit quand [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] n'est pas installé correctement sur l'ordinateur que vous tentez de déboguer. Cela peut signifier qu'[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] n'a jamais été installé ou qu'[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] a été installé avant les services IIS (Internet Information Services).  
  
### <a name="to-reinstall-aspnet"></a>Pour réinstaller ASP.NET  
  
1. À partir d'une invite de commandes, exécutez la commande suivante :  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     où *version* représente le numéro de version du .NET Framework installée sur votre ordinateur, par exemple v1.0.370. Vous pouvez déterminer la version du framework en consultant le `\WINDOWS\Microsoft.NET\Framework` directory.  
  
    > [!NOTE]
    > Sous Windows Server 2003, vous pouvez installer [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] avec **Ajout/Suppression de programmes** dans le Panneau de configuration.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’applications web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
