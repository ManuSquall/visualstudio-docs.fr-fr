---
title: Débogage d’Applications ASP.NET déployées | Documents Microsoft
ms.custom: ''
ms.date: 06/30/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: b8c7c9ea2f280eaf60f4592f149ed2989d862b9b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="debugging-deployed-aspnet-applications"></a>Débogage des Applications ASP.NET déployées
Pour utiliser [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour déboguer une application déployée, vous devez créer un attachement au processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] et vous assurer que le débogueur a accès aux symboles de l'application. Vous devez également rechercher et ouvrir les fichiers sources pour l'application. Pour plus d’informations, consultez [spécifier de symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [Comment : rechercher le nom du processus ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md), et [requise](../debugger/aspnet-debugging-system-requirements.md).  

> [!WARNING]
> Si vous attachez à la [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processus de travail pour le débogage et atteint un point d’arrêt, tout le code managé dans le processus de travail s’arrête. Un arrêt de tout le code managé dans le processus de travail peut provoquer un arrêt de traitement pour tous les utilisateurs sur le serveur. Avant d'effectuer un débogage sur un serveur de production, considérez l'impact potentiel sur le travail de production. 
  
La procédure d'attachement au processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] est identique à l'attachement à tout autre processus distant. Lorsque vous êtes attaché, si le projet approprié n’est pas ouvert, une boîte de dialogue s’affiche lorsque l’application s’arrête. Elle vous demande d'indiquer l'emplacement des fichiers sources pour l'application. Le nom de fichier que vous spécifiez dans la boîte de dialogue doit correspondre au nom de fichier spécifié dans les symboles de débogage, situés sur le serveur web. Pour plus d’informations, consultez [attacher au processus en cours](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). Pour configurer le débogage distant sur IIS, consultez [ASP.NET de débogage à distance sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).
 
> [!NOTE]
>  De nombreuses applications Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] font référence à des DLL qui contiennent une logique métier ou un autre code utile. Une telle référence copie la DLL dans le dossier \bin du répertoire virtuel de l’application Web à partir de votre ordinateur local lorsque vous déployez votre application. Lorsque vous effectuez un débogage, rappelez-vous que votre application Web référence cette copie de la DLL et non pas celle qui se trouve sur votre ordinateur local. 
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’Applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Comment : activer le débogage pour les Applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Comment : rechercher le nom du processus ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [Spécifiez les symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)