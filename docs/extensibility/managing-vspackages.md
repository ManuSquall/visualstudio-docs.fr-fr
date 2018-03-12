---
title: Gestion des VSPackages | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: "35"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3c3201c032d0cae645460e614b6d4138297e4a93
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="managing-vspackages"></a>Gestion des VSPackages
Dans la plupart des cas vous n’avez pas à vous soucier de la gestion des VSPackages, étant donné que les modèles de projet et d’élément enregistrement et chargent le package automatiquement. Toutefois, dans certains cas, vous devrez peut-être en savoir un peu plus pour gérer votre package.  
  
## <a name="using-the-experimental-instance"></a>À l’aide de l’instance expérimentale  
 Pour plus d’informations sur l’instance expérimentale, consultez [l’Instance expérimentale](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Inscription et annulation de l’inscription de VSPackages  
 Pour savoir comment enregistrer et annuler l’inscription de VSPackages et autres types d’extensions, consultez [inscription et annulation de l’inscription de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Le chargement d’un VSPackage  
 Les VSPackages peuvent être définies à autoload lorsque certains que CMDUICONTEXT GUID est activée. Pour plus d’informations, consultez [le chargement des VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>À l’aide de AsyncPackage pour charger les VSPackages en arrière-plan  
 La classe AsyncPackage permet package charger sur un thread d’arrière-plan pour une meilleure réactivité de l’interface utilisateur dans Visual Studio. Pour plus d’informations, consultez [Comment : AsyncPackage d’utilisation pour les VSPackages de chargement en arrière-plan](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Contexte de l’interface utilisateur basée sur une règle pour les Extensions  
 Contextes d’interface utilisateur basée sur des règles autorise les auteurs d’extension définir les conditions précises sous lequel un contexte de l’interface utilisateur est activé et chargé de VSPackages associés. Pour plus d’informations, consultez [Comment : contexte d’interface utilisateur basée sur une règle de l’utilisation d’Extensions Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="diagnosing-extension-performance"></a>Diagnostiquer les performances de l’extension  
Les extensions peuvent affecter les performances de charge de démarrage et de la solution. Découvrez comment l’impact d’extension de Visual Studio est calculée et comment il peut être analysé localement pour tester si une extension peut s’afficher à l’extension de compromettre des performances. Pour plus d’informations, consultez [Comment : diagnostiquer les performances Extension](how-to-diagnose-extension-performance.md). 
  
## <a name="troubleshooting-vspackages"></a>Dépanner les packages VS  
 Découvrez les techniques de dépannage des VSPackages qui ne sont pas chargés ou rencontrent des erreurs : [VSPackages de résolution des problèmes](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages](../extensibility/internals/vspackages.md)