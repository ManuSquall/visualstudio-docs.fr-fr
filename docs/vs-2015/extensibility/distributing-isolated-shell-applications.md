---
title: Distribution d’applications Shell isolées | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf0d8a4cab8d30a56e84d1a6869c2c842b982aea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204674"
---
# <a name="distributing-isolated-shell-applications"></a>Distribution d’applications avec Shell isolé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous devez installer Visual Studio et le kit de développement logiciel (SDK) Visual Studio pour créer une application Shell isolée. Pour distribuer l’application aux ordinateurs d’autres utilisateurs ou clients, vous devez inclure un package redistribuable spécial pour l’interpréteur de commandes isolé.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Conditions préalables à la distribution d’applications Shell isolées  
  
|Nom|Description|  
|----------|-----------------|  
|Kit de développement logiciel Visual Studio|Le kit de développement logiciel (SDK) dont vous avez besoin pour développer et tester les extensions de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Vous pouvez également utiliser le kit de développement logiciel (SDK) pour créer votre propre instance du shell isolé Visual Studio.<br /><br /> Visual Studio est un composant requis pour le kit de développement logiciel (SDK).|  
|Redistribuable de l’interpréteur de commandes Microsoft Visual Studio isolé|Le package redistribuable que vous incluez dans votre programme d’installation lorsque vous créez un environnement d’outils sur le shell isolé Visual Studio. Le package redistribuable de l’interpréteur de commandes isolé comprend les .NET Framework 4,5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Création d’un programme d’installation pour l’application  
 Vous devez créer un programme d’installation spécial pour votre application shell intégrée ou isolée. Pour plus d’informations, consultez [installation d’une application Shell isolée](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Autorisation des mises à jour de votre application  
 Votre programme d’installation doit autoriser la mise à jour de votre application, soit par Microsoft Updates, soit par les mises à jour de votre entreprise. Pour plus d’informations sur les mises à jour, consultez [instructions de maintenance pour les applications de Shell isolé](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).
