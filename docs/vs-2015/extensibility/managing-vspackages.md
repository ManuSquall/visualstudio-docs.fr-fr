---
title: Gestion de VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8cb96dfbdecd5182d328d425a209f52833ede23c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781593"
---
# <a name="managing-vspackages"></a>Gestion de VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans la plupart des cas vous n’avez pas besoin à vous soucier de la gestion des VSPackages, étant donné que les modèles de projet et d’élément enregistrer et chargent le package automatiquement. Toutefois, dans certains cas, vous devrez peut-être pour en savoir un peu plus pour gérer votre package.  
  
## <a name="using-the-experimental-instance"></a>À l’aide de l’instance expérimentale  
 Pour en savoir plus sur l’instance expérimentale, consultez [l’Instance expérimentale](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Inscription et désinscription de VSPackages  
 Pour savoir comment procéder inscrire et désinscrire des VSPackages et autres types d’extensions, consultez [inscription et annulation de l’inscription de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Le chargement d’un VSPackage  
 Les VSPackages peuvent être définies pour charger automatiquement lorsqu’un particulier que CMDUICONTEXT GUID est activé. Pour plus d’informations, consultez [le chargement de VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>À l’aide de AsyncPackage pour charger des VSPackages en arrière-plan  
 La classe AsyncPackage permet de package à charger sur un thread d’arrière-plan pour une meilleure réactivité de l’interface utilisateur dans Visual Studio. Pour plus d’informations, consultez [Comment : AsyncPackage utilisation aux VSPackages de chargement en arrière-plan](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Contexte d’interface utilisateur basée sur une règle pour les Extensions  
 Contextes d’interface utilisateur basée sur des règles permet aux auteurs d’extension définir les conditions précises sous lesquelles un contexte d’interface utilisateur est activé et chargé de VSPackages associés. Pour plus d’informations, consultez [Comment : contexte d’interface utilisateur basée sur la règle de l’utilisation d’Extensions Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="troubleshooting-vspackages"></a>Dépannage de VSPackages  
 Découvrez les techniques permettant de dépanner les packages VS qui ne se chargent pas ou que vous rencontrez des erreurs : [VSPackages de résolution des problèmes](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages](../extensibility/internals/vspackages.md)

