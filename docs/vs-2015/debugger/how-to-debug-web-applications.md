---
title: 'Comment : déboguer des applications Web | Microsoft Docs'
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
- Web services, debugging
- ASP.NET Web Forms, debugging
- ASP.NET, debugging Web applications
- debugging ASP.NET Web applications, during development
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd3cbbcd740c0f124b8ab4379204a9d425cd541c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205404"
---
# <a name="how-to-debug-web-applications"></a>Comment : déboguer des applications Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] est la principale technologie pour le développement d’applications Web dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Le débogueur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fournit des outils puissants pour le débogage d'applications Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] localement ou sur un serveur distant. Cette rubrique décrit comment déboguer un [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] projet pendant le développement. Pour plus d’informations sur le débogage d’une [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] application Web déjà déployée sur un serveur de production, consultez [débogage d’applications Web déployées](../debugger/debugging-deployed-web-applications.md).  
  
 Pour déboguer une application [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] :  
  
- Vous devez disposer des autorisations requises. Pour plus d’informations, consultez [Configuration système requise](../debugger/aspnet-debugging-system-requirements.md).  
  
- [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] le débogage doit être activé dans les **Propriétés du projet**.  
  
- Le fichier de configuration de votre application (Web.config) doit avoir pour valeur mode débogage. En mode débogage, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] génère des symboles pour les fichiers générés dynamiquement et le débogueur peut être attaché à l'application [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] définit cela automatiquement lorsque vous commencez le débogage, si vous avez créé votre projet à partir du modèle de projets Web.  
  
- Pour plus d’informations, consultez [Comment : activer le débogage pour les Applications ASP.net](../debugger/how-to-enable-debugging-for-aspnet-applications.md).  
  
### <a name="to-debug-a-web-application-during-development"></a>Pour déboguer une application Web lors du développement  
  
1. Dans le menu **Déboguer** , cliquez sur **Démarrer** pour commencer le débogage de l’application Web.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] génère le projet d’application Web, déploie l’application si nécessaire, démarre le Serveur de développement ASP.NET si vous effectuez un débogage localement et s’attache au [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] processus de travail.  
  
2. Utilisez le débogueur pour définir et effacer les points d'arrêt, effectuer du pas à pas et d'autres opérations de débogage, comme pour n'importe quelle application.  
  
     Pour plus d’informations, consultez [concepts de base du débogueur](../debugger/debugger-basics.md).  
  
3. Dans le menu **Déboguer** , cliquez sur **arrêter le débogage** pour mettre fin à la session de débogage, ou, dans le menu **fichier** d’Internet Explorer, cliquez sur **Fermer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’applications et de scripts Web](../debugger/debugging-web-applications-and-script.md)   
 [Débogage d’applications ASP.NET et AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Comment :  activer le débogage pour les applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
