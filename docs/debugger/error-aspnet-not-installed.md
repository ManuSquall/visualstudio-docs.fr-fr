---
title: 'Erreur : ASP.NET ne pas installé | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 34ef8ef597c21230aa9ccdbd3146c07825753879
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680592"
---
# <a name="error-aspnet-not-installed"></a>Erreur : ASP.NET n'est pas installé
Cette erreur se produit quand [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] n'est pas installé correctement sur l'ordinateur que vous tentez de déboguer. Cela peut signifier qu'[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] n'a jamais été installé ou qu'[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] a été installé avant les services IIS (Internet Information Services).

### <a name="to-reinstall-aspnet"></a>Pour réinstaller ASP.NET

1. À partir d'une invite de commandes, exécutez la commande suivante :

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    où *version* représente le numéro de version du .NET Framework installée sur votre ordinateur, par exemple v1.0.370. Vous pouvez déterminer la version du framework en consultant le `\WINDOWS\Microsoft.NET\Framework` directory.

   > [!NOTE]
   >  Sous Windows Server 2003, vous pouvez installer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] avec **Ajout/Suppression de programmes** dans le Panneau de configuration.

## <a name="see-also"></a>Voir aussi
- [Débogage d’applications web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
