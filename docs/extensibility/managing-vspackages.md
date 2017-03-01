---
title: La gestion de packages VS | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 32e4aa4302f7871e71907d094c12038b00d7e6bb
ms.lasthandoff: 02/22/2017

---
# <a name="managing-vspackages"></a>La gestion de packages VS
Dans la plupart des cas vous n’avez pas à vous soucier de la gestion de packages VS, étant donné que les modèles de projet et d’élément enregistrer et chargent le package automatiquement. Toutefois, dans certains cas vous devrez peut-être en savoir un peu plus pour gérer votre package.  
  
## <a name="using-the-experimental-instance"></a>À l’aide de l’instance expérimentale  
 Pour plus d’informations sur l’instance expérimentale, consultez la page [l’Instance expérimentale](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Inscription et annulation de l’enregistrement de packages VS  
 Pour savoir comment inscrire et désinscrire des VSPackages et autres types d’extensions, consultez [inscription et annulation de l’enregistrement de packages VS](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Le chargement d’un VSPackage  
 Les VSPackages peut être définies à chargement automatique lorsqu’un particulier que CMDUICONTEXT GUID est activée. Pour plus d’informations, consultez [le chargement de packages VS](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>L’utilisation de AsyncPackage pour charger les VSPackages en arrière-plan  
 La classe AsyncPackage permet de package à charger sur un thread d’arrière-plan pour une meilleure réactivité de l’interface utilisateur dans Visual Studio. Pour plus d’informations, consultez [Comment : AsyncPackage utilisé pour charger les VSPackages en arrière-plan](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Contexte de l’interface utilisateur basée sur des règles pour les Extensions  
 Contextes d’interface utilisateur basée sur des règles permet aux auteurs d’extension définir les conditions précises sous lequel un contexte de l’interface utilisateur est activé et chargé VSPackages associés. Pour plus d’informations, consultez [Comment : contexte de l’interface utilisateur basée sur la règle de l’utilisation d’Extensions Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="diagnosing-extension-performance"></a>Diagnostic des performances de l’extension  
Les extensions peuvent affecter les performances de charge de solution et de démarrage. Découvrez comment l’impact d’extension de Visual Studio est calculée et comment il peut être analysé en local pour tester si une extension peut s’afficher comme une extension aient un impact sur des performances. Pour plus d’informations, consultez [Comment : diagnostiquer les performances Extension](how-to-diagnose-extension-performance.md). 
  
## <a name="troubleshooting-vspackages"></a>Dépanner les packages VS  
 Découvrez les techniques permettant de dépanner les packages VS qui ne sont pas chargés ou rencontrent des erreurs : [VSPackages de résolution des problèmes](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Packages VS](../extensibility/internals/vspackages.md)
