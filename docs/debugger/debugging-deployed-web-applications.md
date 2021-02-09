---
title: Débogage des applications ASP.NET déployées | Microsoft Docs
description: Utilisez Visual Studio pour déboguer une application ASP.NET déployée en l’attachant au processus de travail et en veillant à ce que le débogueur ait accès aux symboles de l’application.
ms.custom: SEO-VS-2020
ms.date: 06/30/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 9b298d756754743635fe3de10c8b72d3195ff3f8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872805"
---
# <a name="debugging-deployed-aspnet-applications"></a>Débogage des applications ASP.NET déployées
Pour utiliser [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour déboguer une application déployée, vous devez créer un attachement au processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] et vous assurer que le débogueur a accès aux symboles de l'application. Vous devez également rechercher et ouvrir les fichiers sources pour l'application. Pour plus d’informations, consultez [spécifier les fichiers de symboles (. pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [Comment : Rechercher le nom du processus ASP.net](../debugger/how-to-find-the-name-of-the-aspnet-process.md)et la [Configuration système requise](../debugger/aspnet-debugging-system-requirements.md).

> [!WARNING]
> Si vous attachez au [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processus de travail pour le débogage et que vous atteignez un point d’arrêt, l’ensemble du code managé dans le processus de travail s’arrête. Un arrêt de tout le code managé dans le processus de travail peut provoquer un arrêt de traitement pour tous les utilisateurs sur le serveur. Avant d'effectuer un débogage sur un serveur de production, considérez l'impact potentiel sur le travail de production.

La procédure d'attachement au processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] est identique à l'attachement à tout autre processus distant. Quand vous êtes attaché, si le projet approprié n’est pas ouvert, une boîte de dialogue apparaît quand l’application s’arrête. Elle vous demande d'indiquer l'emplacement des fichiers sources pour l'application. Le nom de fichier que vous spécifiez dans la boîte de dialogue doit correspondre au nom de fichier spécifié dans les symboles de débogage, situés sur le serveur Web. Pour plus d’informations, consultez [attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). Pour configurer le débogage distant sur IIS, consultez [débogage à distance ASP.net sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

> [!NOTE]
> De nombreuses applications Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] font référence à des DLL qui contiennent une logique métier ou un autre code utile. Une telle référence copie la DLL de votre ordinateur local dans le dossier \Bin du répertoire virtuel de l’application Web lorsque vous déployez votre application. Lorsque vous effectuez un débogage, rappelez-vous que votre application Web référence cette copie de la DLL et non pas celle qui se trouve sur votre ordinateur local.

## <a name="see-also"></a>Voir aussi
- [Déboguer des applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Comment :  activer le débogage pour les applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Comment : Rechercher le nom du processus ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)
- [Spécifier les fichiers de symboles (.pdb) et les fichiers source](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)