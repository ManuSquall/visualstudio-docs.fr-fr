---
title: 'Débogage ASP.NET : Configuration requise | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16fcebe8ecb5fff974d5df6e2405acca546ea007
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793800"
---
# <a name="aspnet-debugging-system-requirements"></a>Débogage ASP.NET : configuration requise
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique décrit les conditions de sécurité et les logiciels requis pour les scénarios de débogage de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] :  
  
-   Débogage local, dans lequel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et l'application Web s'exécutent sur le même ordinateur. Il y a deux versions de ce scénario :  
  
    -   Le code [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] réside sur le système de fichiers.  
  
    -   Le code de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] réside sur un site Web IIS.  
  
-   Débogage distant, dans lequel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] s'exécute sur un ordinateur client et débogue une application Web qui s'exécute sur un ordinateur de serveur distant.  
  
## <a name="security-requirements"></a>Conditions de sécurité  
 Pour le débogage distant, les ordinateurs locaux et distants doivent être sur une installation de domaine ou une installation de groupe de travail.  
  
 Pour déboguer le processus de traitement [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] , vous devez disposer de l'autorisation pour déboguer ce processus. Par défaut, les applications [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] s'exécutent en tant qu'utilisateur **ASPNET** . Si le processus de traitement s'exécute en tant qu' **ASPNET**ou que **SERVICE RÉSEAU**, vous devez disposer de droits d'administrateur pour le déboguer.  
  
 Le nom du processus de traitement [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] varie en fonction du scénario de débogage et de la version d'IIS. Pour plus d'informations, consultez [How to: Find the Name of the ASP.NET Process](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Vous pouvez changer le compte d'utilisateur sous lequel s'exécute le processus de travail [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] en modifiant le fichier machine.config sur le serveur qui exécute IIS. La meilleure façon de procéder consiste à utiliser le **Gestionnaire IIS**. Pour plus d’informations, consultez [Comment : exécuter le travail processus sous un compte d’utilisateur](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Si vous modifiez le processus de traitement [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pour qu'il s'exécute sous votre propre compte d'utilisateur, vous n'avez pas besoin d'être administrateur sur le serveur qui exécute IIS.  
  
> [!CAUTION]
>  Avant de modifier le processus de traitement [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pour qu'il s'exécute sous un compte différent, envisagez les conséquences que pourrait avoir un piratage du processus de traitement [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] lors de son exécution sous ce compte. Les comptes d'utilisateur ASPNET et SERVICE RÉSEAU s'exécutent avec des autorisations minimales, réduisant les dommages possibles en cas de piratage du processus. Si vous devez modifier le processus de traitement [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pour qu'il s'exécute sous un compte qui a des autorisations supérieures, le risque de dommage est accru.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage des Applications ASP.NET et AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Guide pratique pour exécuter le processus Worker sous un compte d’utilisateur](../debugger/how-to-run-the-worker-process-under-a-user-account.md)



