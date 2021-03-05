---
description: Cette erreur se produit lorsque ASP.NET n’est pas installé correctement sur l’ordinateur que vous essayez de déboguer.
title: ASP.NET n’est pas installé
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.http_not_supported
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 205f0fb3948414ec87b735af9b1b97917872a950
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147053"
---
# <a name="error-aspnet-not-installed"></a>Erreur : ASP.NET n'est pas installé
Cette erreur se produit quand [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] n'est pas installé correctement sur l'ordinateur que vous tentez de déboguer. Cela peut signifier qu'[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] n'a jamais été installé ou qu'[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] a été installé avant les services IIS (Internet Information Services).

### <a name="to-reinstall-aspnet"></a>Pour réinstaller ASP.NET

1. À partir d'une invite de commandes, exécutez la commande suivante :

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    où *version* représente le numéro de version du .NET Framework installé sur votre ordinateur, par exemple v 1.0.370. Vous pouvez déterminer la version du Framework en regardant dans le `\WINDOWS\Microsoft.NET\Framework` répertoire.

   > [!NOTE]
   > Sous Windows Server 2003, vous pouvez installer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] avec **Ajout/Suppression de programmes** dans le Panneau de configuration.

## <a name="see-also"></a>Voir aussi
- [Débogage d'applications Web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
