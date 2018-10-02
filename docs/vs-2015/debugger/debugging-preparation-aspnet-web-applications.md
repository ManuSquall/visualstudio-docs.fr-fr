---
title: 'Préparation du débogage : Des Applications Web ASP.NET | Microsoft Docs'
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
- VB
- CSharp
helpviewer_keywords:
- debugging ASP.NET Web applications
- debugging [Visual Studio], Web applications
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 38
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20731f5036a89c3c19fbea0d825d67fc02c13cf9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504094"
---
# <a name="debugging-preparation-aspnet-web-applications"></a>Préparation du débogage : applications Web ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [préparation du débogage : Applications Web ASP.NET](https://docs.microsoft.com/visualstudio/debugger/debugging-preparation-aspnet-web-applications).  
  
Le [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]modèle de site Web crée une application Web Form. Lorsque vous créez un site Web à l'aide de ce modèle, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] crée les paramètres par défaut pour le débogage. Dans le **propriétés du projet** boîte de dialogue, vous pouvez spécifier si vous souhaitez que la page Web soit une page de démarrage. Lorsque vous commencez à déboguer un [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Site Web avec ces paramètres par défaut, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] démarre Internet Explorer et attache le débogueur à la [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] des processus de travail (aspnet_wp.exe ou w3wp.exe). Pour plus d’informations, consultez [requise](../debugger/aspnet-debugging-system-requirements.md).  
  
### <a name="to-create-a-web-forms-application"></a>Pour créer une application Web Forms  
  
1.  Sur le **fichier** menu, choisissez **nouveau Site Web**.  
  
2.  Dans le **nouveau Site Web** boîte de dialogue, sélectionnez [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] **Site Web**.  
  
3.  Cliquez sur **OK**.  
  
### <a name="to-debug-your-web-form"></a>Pour déboguer votre Web Form  
  
1.  Définissez un ou plusieurs points d'arrêt dans vos fonctions et gestionnaires d'événements.  
  
     Pour plus d'informations, consultez [Breakpoints and Tracepoints](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  Lorsqu'un point d'arrêt est atteint, parcourez le code à l'intérieur de la fonction. Observez l'exécution de votre code jusqu'à cerner le problème.  
  
     Pour plus d’informations, consultez [exécution pas à pas](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9) et [le débogage des Applications Web et scripts](../debugger/debugging-web-applications-and-script.md).  
  
## <a name="changing-default-configurations"></a>Modification des configurations par défaut  
 Si vous le souhaitez, vous êtes autorisé à modifier les valeurs par défaut des configurations Debug et Release créées par [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Pour plus d’informations, consultez [Guide pratique pour définir des configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### <a name="to-change-the-default-debug-configuration"></a>Pour modifier la configuration Debug par défaut  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le site Web et sélectionnez **Pages de propriétés** pour ouvrir le **Pages de propriétés** boîte de dialogue.  
  
2.  Cliquez sur **Options de démarrage**.  
  
3.  Définissez **Action de démarrage** à la page Web qui doit être affichée en premier.  
  
4.  Sous **débogueurs**, assurez-vous que **débogage ASP.NET** est sélectionné.  
  
     Pour plus d’informations, consultez [paramètres des Pages de propriété pour les projets Web](../debugger/property-pages-settings-for-web-projects.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)   
 [Principes de base du débogueur](../debugger/debugger-basics.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Débogage du code managé](../debugger/debugging-managed-code.md)



