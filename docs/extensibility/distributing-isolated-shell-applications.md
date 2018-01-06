---
redirect_url: shell/distributing-isolated-shell-applications
title: "Distribution d’Applications de Shell isolé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 250f1d7769f6035e015eeb7247c439b27f913b78
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="distributing-isolated-shell-applications"></a>Distribution d’Applications de Shell isolé
Vous devez installer Visual Studio et le Kit de développement logiciel Visual Studio pour créer une application de shell isolé. Pour distribuer l’application pour les ordinateurs d’autres utilisateurs ou des clients, vous devez inclure un package redistribuable spéciale pour le shell isolé.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Conditions préalables requises pour distribuer des Applications de Shell isolé  
  
|Name|Description|  
|----------|-----------------|  
|SDK Visual Studio|Le SDK, vous devez disposer pour développer et tester des extensions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Vous pouvez également utiliser le Kit de développement pour créer votre propre instance du shell isolé Visual Studio.<br /><br /> Visual Studio est un composant requis pour le Kit de développement.|  
|Microsoft Visual Studio isolé redistribuable de l’interpréteur de commandes|Shell isolé redistribuables que vous incluez dans votre programme d’installation lorsque vous générez un environnement d’outils dans Visual Studio. Le package redistribuable de Shell isolé inclut le .NET Framework 4.5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Création d’un programme d’Installation de l’Application  
 Vous devez créer un programme d’installation spéciales pour votre application de shell intégré ou isolé. Pour plus d’informations, consultez [installation d’une Application de Shell isolé](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Autoriser les mises à jour à votre Application  
 Le programme d’installation doit permettre la possibilité que votre application sera être mis à jour, mises à jour Microsoft ou par les mises à jour de votre entreprise. Pour plus d’informations sur les mises à jour, consultez [de maintenance des recommandations pour les Applications de Shell isolé](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).