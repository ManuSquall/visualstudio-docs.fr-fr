---
title: Gestion de VSPackages | Microsoft Docs
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194376"
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
 La classe AsyncPackage permet de package à charger sur un thread d’arrière-plan pour une meilleure réactivité de l’interface utilisateur dans Visual Studio. Pour plus d'informations, voir [Procédure : Utiliser AsyncPackage pour charger des VSPackages en arrière-plan](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Contexte d’interface utilisateur basée sur une règle pour les Extensions  
 Contextes d’interface utilisateur basée sur des règles permet aux auteurs d’extension définir les conditions précises sous lesquelles un contexte d’interface utilisateur est activé et chargé de VSPackages associés. Pour plus d’informations, consultez [Guide pratique pour Utiliser le contexte de l’interface utilisateur basée sur une règle pour les Extensions Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="troubleshooting-vspackages"></a>Dépannage de VSPackages  
 Découvrez les techniques permettant de dépanner les packages VS qui ne se chargent pas ou que vous rencontrez des erreurs : [Dépannage de VSPackages](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages](../extensibility/internals/vspackages.md)
