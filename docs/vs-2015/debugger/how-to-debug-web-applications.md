---
title: 'Procédure : Déboguer des Applications Web | Microsoft Docs'
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205404"
---
# <a name="how-to-debug-web-applications"></a>Procédure : Déboguer des applications Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] est la principale technologie pour le développement d’applications Web dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Le débogueur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fournit des outils puissants pour le débogage d'applications Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] localement ou sur un serveur distant. Cette rubrique décrit comment déboguer un [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] projet pendant le développement. Pour plus d’informations sur la façon de déboguer un [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web application déjà déployée sur un serveur de production, consultez [débogage des Applications Web déployées](../debugger/debugging-deployed-web-applications.md).  
  
 Pour déboguer une application [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] :  
  
- Vous devez disposer des autorisations requises. Pour plus d'informations, voir [System Requirements](../debugger/aspnet-debugging-system-requirements.md).  
  
- [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] le débogage doit être activé dans **propriétés du projet**.  
  
- Le fichier de configuration de votre application (Web.config) doit avoir pour valeur mode débogage. En mode débogage, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] génère des symboles pour les fichiers générés dynamiquement et le débogueur peut être attaché à l'application [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] définit cela automatiquement lorsque vous commencez le débogage, si vous avez créé votre projet à partir du modèle de projets Web.  
  
- Pour plus d’informations, consultez [Guide pratique pour Activer le débogage pour les Applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md).  
  
### <a name="to-debug-a-web-application-during-development"></a>Pour déboguer une application Web lors du développement  
  
1. Sur le **déboguer** menu, cliquez sur **Démarrer** pour commencer le débogage de l’application Web.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] génère le projet d'application Web, déploie l'application si nécessaire, démarre le serveur de développement ASP.NET si vous effectuez un débogage localement, et crée un attachement au processus de traitement [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
2. Utilisez le débogueur pour définir et effacer les points d'arrêt, effectuer du pas à pas et d'autres opérations de débogage, comme pour n'importe quelle application.  
  
     Pour plus d’informations, consultez [principes fondamentaux du débogueur](../debugger/debugger-basics.md).  
  
3. Sur le **déboguer** menu, cliquez sur **arrêter le débogage** à la fin de la session de débogage, ou, dans le **fichier** menu dans Internet Explorer, cliquez sur **fermer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’applications et de scripts web](../debugger/debugging-web-applications-and-script.md)   
 [Débogage d’applications ASP.NET et AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Guide pratique pour activer le débogage pour les applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
