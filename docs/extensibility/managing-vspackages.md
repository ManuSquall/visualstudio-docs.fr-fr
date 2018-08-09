---
title: Gestion de VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14aa17f4692857d650cb3bc9fe1a3498fc4f147a
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639558"
---
# <a name="manage-vspackages"></a>Gérer les packages VS
Dans la plupart des cas vous n’avez pas besoin à vous soucier de la gestion des VSPackages, étant donné que les modèles de projet et d’élément enregistrer et chargent le package automatiquement. Toutefois, dans certains cas, vous devrez peut-être pour en savoir un peu plus pour gérer votre package.  
  
## <a name="use-the-experimental-instance"></a>Utiliser l’instance expérimentale  
 Pour en savoir plus sur l’instance expérimentale, consultez [l’instance expérimentale](../extensibility/the-experimental-instance.md).  
  
## <a name="register-and-unregister-vspackages"></a>Inscrire et désinscrire des VSPackages  
 Pour savoir comment procéder inscrire et désinscrire des VSPackages et autres types d’extensions, consultez [inscrire et désinscrire des VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="load-a-vspackage"></a>Charger un VSPackage  
 Les VSPackages peuvent être définies pour charger automatiquement lorsqu’un particulier que CMDUICONTEXT GUID est activé. Pour plus d’informations, consultez [charge VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Utiliser AsyncPackage pour charger des VSPackages en arrière-plan  
 Le `AsyncPackage` classe permet le chargement de package sur un thread d’arrière-plan pour une meilleure réactivité de l’interface utilisateur dans Visual Studio. Pour plus d’informations, consultez [Comment : utiliser des AsyncPackage pour charger des VSPackages en arrière-plan](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Contexte d’interface utilisateur basée sur une règle pour les extensions  
 Contextes d’interface utilisateur basée sur des règles permet aux auteurs d’extension définir les conditions précises sous lesquelles un contexte d’interface utilisateur est activé et chargé de VSPackages associés. Pour plus d’informations, consultez [Comment : utiliser le contexte d’interface utilisateur basée sur une règle pour les extensions Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="diagnose-extension-performance"></a>Diagnostiquer les performances de l’extension  
Extensions peuvent affecter les performances de chargement de solution et de démarrage. Découvrez comment l’impact d’extension de Visual Studio est calculée et comment elles peuvent être analysées localement pour tester si une extension peut être affichée comme une extension d’ayant un impact sur des performances. Pour plus d’informations, consultez [Comment : diagnostiquer les performances de l’extension](how-to-diagnose-extension-performance.md). 
  
## <a name="troubleshoot-vspackages"></a>Résoudre les problèmes de VSPackages  
 Découvrez les techniques permettant de dépanner les packages VS qui ne se chargent pas ou que vous rencontrez des erreurs : [résoudre les problèmes de VSPackages](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages](../extensibility/internals/vspackages.md)