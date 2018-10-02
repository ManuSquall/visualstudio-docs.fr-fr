---
title: 'Débogage ASP.NET : Configuration requise | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f5386390261028fd635f93bc06d3a3fc8805ebdd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493435"
---
# <a name="aspnet-debugging-system-requirements"></a>Débogage ASP.NET : configuration requise
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [débogage ASP.NET : configuration système requise](https://docs.microsoft.com/visualstudio/debugger/aspnet-debugging-system-requirements).  
  
Cette rubrique décrit les exigences de sécurité et les logiciels pour [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] scénarios de débogage :  
  
-   Débogage local, dans lequel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et l'application Web s'exécutent sur le même ordinateur. Il y a deux versions de ce scénario :  
  
    -   Le code [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] réside sur le système de fichiers.  
  
    -   Le code de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] réside sur un site Web IIS.  
  
-   Débogage distant, dans lequel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] s'exécute sur un ordinateur client et débogue une application Web qui s'exécute sur un ordinateur de serveur distant.  
  
## <a name="security-requirements"></a>Conditions de sécurité  
 Pour le débogage distant, les ordinateurs locaux et distants doivent être sur une installation de domaine ou une installation de groupe de travail.  
  
 Pour déboguer le processus de traitement [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], vous devez disposer de l'autorisation pour déboguer ce processus. Par défaut, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] applications s’exécutent en tant que le **ASPNET** utilisateur. Si le processus de traitement s'exécute en tant qu' **ASPNET**ou que **SERVICE RÉSEAU**, vous devez disposer de droits d'administrateur pour le déboguer.  
  
 Le nom du processus de traitement [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] varie en fonction du scénario de débogage et de la version d'IIS. Pour plus d'informations, consultez [How to: Find the Name of the ASP.NET Process](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Vous pouvez changer le compte d'utilisateur sous lequel s'exécute le processus de travail [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] en modifiant le fichier machine.config sur le serveur qui exécute IIS. La meilleure façon de procéder consiste à utiliser le **Gestionnaire IIS**. Pour plus d’informations, consultez [Comment : exécuter le travail processus sous un compte d’utilisateur](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Si vous modifiez le processus de traitement [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pour qu'il s'exécute sous votre propre compte d'utilisateur, vous n'avez pas besoin d'être administrateur sur le serveur qui exécute IIS.  
  
> [!CAUTION]
>  Avant de modifier le processus de traitement [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pour qu'il s'exécute sous un compte différent, envisagez les conséquences que pourrait avoir un piratage du processus de traitement [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] lors de son exécution sous ce compte. Les comptes d'utilisateur ASPNET et SERVICE RÉSEAU s'exécutent avec des autorisations minimales, réduisant les dommages possibles en cas de piratage du processus. Si vous devez modifier le processus de traitement [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pour qu'il s'exécute sous un compte qui a des autorisations supérieures, le risque de dommage est accru.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage des Applications ASP.NET et AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Guide pratique pour exécuter le processus Worker sous un compte d’utilisateur](../debugger/how-to-run-the-worker-process-under-a-user-account.md)



