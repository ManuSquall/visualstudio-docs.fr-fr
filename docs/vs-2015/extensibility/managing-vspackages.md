---
title: Gestion des VSPackages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b56ab490342cfbda9c16408aa0937abd80728c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194376"
---
# <a name="managing-vspackages"></a>Gestion de VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans la plupart des cas, vous n’avez pas à vous soucier de la gestion des VSPackages, puisque les modèles de projet et d’élément s’inscrivent et chargent automatiquement le package. Toutefois, dans certains cas, vous devrez peut-être en apprendre un peu plus pour gérer votre package.  
  
## <a name="using-the-experimental-instance"></a>Utilisation de l’instance expérimentale  
 Pour en savoir plus sur l’instance expérimentale, consultez [l’instance expérimentale](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Inscription et désinscription de VSPackages  
 Pour savoir comment inscrire et désinscrire des VSPackages et d’autres types d’extension, consultez [inscription et annulation](../extensibility/registering-and-unregistering-vspackages.md)de l’inscription de VSPackages.  
  
## <a name="loading-a-vspackage"></a>Chargement d’un VSPackage  
 Les VSPackages peuvent être définis sur autoload lorsqu’un GUID CMDUICONTEXT particulier est activé. Pour plus d’informations, consultez [chargement des VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Utilisation de AsyncPackage pour charger les VSPackages en arrière-plan  
 La classe AsyncPackage active le chargement des packages sur un thread d’arrière-plan pour une meilleure réactivité de l’interface utilisateur dans Visual Studio. Pour plus d’informations, consultez [Comment : utiliser AsyncPackage pour charger des VSPackages en arrière-plan](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Contexte de l’interface utilisateur basé sur des règles pour les extensions  
 Les contextes d’interface utilisateur basés sur des règles permettent aux auteurs d’extensions de définir les conditions précises sous lesquelles un contexte d’interface utilisateur est activé et les VSPackages associés chargés. Pour plus d’informations, consultez [Comment : utiliser le contexte de l’interface utilisateur basé sur des règles pour les extensions Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="troubleshooting-vspackages"></a>Dépannage de VSPackages  
 Découvrez les techniques de dépannage des VSPackages qui ne se chargent pas ou qui rencontrent des erreurs : [Dépannage des VSPackages](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages](../extensibility/internals/vspackages.md)
