---
title: Débogage d’applications Web déployées | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9608643801255d6c2cbf278cbfd96908f1f3911d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840164"
---
# <a name="debugging-deployed-web-applications"></a>Débogage d'applications Web déployées
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous devez déboguer une application Web qui s'exécute sur un serveur de production, cela doit être fait avec précaution. Si vous créez un attachement au processus de travail [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pour le débogage et pour atteindre un point d'arrêt, par exemple, tout le code managé dans le processus de traitement s'arrête. Un arrêt de tout le code managé dans le processus de travail peut provoquer un arrêt de traitement pour tous les utilisateurs sur le serveur. Avant d'effectuer un débogage sur un serveur de production, considérez l'impact potentiel sur le travail de production.  
  
 Pour utiliser [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour déboguer une application déployée, vous devez créer un attachement au processus de travail [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] et vous assurer que le débogueur a accès aux symboles de l'application. Vous devez également rechercher et ouvrir les fichiers sources pour l'application. Pour plus d’informations, consultez [spécifier les fichiers de symboles (. pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [Comment : Rechercher le nom du processus ASP.net](../debugger/how-to-find-the-name-of-the-aspnet-process.md)et la [Configuration système requise](../debugger/aspnet-debugging-system-requirements.md).  
  
> [!NOTE]
> De nombreuses applications Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] font référence à des DLL qui contiennent une logique métier ou un autre code utile. Une référence de ce genre copie automatiquement la DLL de votre ordinateur local dans le dossier \bin du répertoire virtuel de l’application Web. Lorsque vous effectuez un débogage, rappelez-vous que votre application Web référence cette copie de la DLL et non pas celle qui se trouve sur votre ordinateur local.  
  
 La procédure d'attachement au processus de travail [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] est identique à l'attachement à tout autre processus distant. Quand vous êtes attaché, si le projet approprié n’est pas ouvert, une boîte de dialogue apparaît quand l’application s’arrête. Elle vous demande d'indiquer l'emplacement des fichiers sources pour l'application. Le nom de fichier que vous spécifiez dans la boîte de dialogue doit correspondre au nom de fichier spécifié dans les symboles de débogage, situés sur le serveur Web. Pour plus d’informations, consultez [attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’applications ASP.NET et AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Débogage d’applications et de scripts Web](../debugger/debugging-web-applications-and-script.md)   
 [Comment : activer le débogage pour les applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Comment : Rechercher le nom du processus ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [Spécifier les fichiers de symboles (.pdb) et les fichiers source](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
