---
title: Distribution d’Applications de Shell isolé | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf0d8a4cab8d30a56e84d1a6869c2c842b982aea
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204674"
---
# <a name="distributing-isolated-shell-applications"></a>Distribution d’applications avec Shell isolé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous devez installer Visual Studio et le Kit de développement logiciel Visual Studio pour créer une application de shell isolé. Pour distribuer l’application sur les ordinateurs d’autres utilisateurs ou des clients, vous devez inclure un package redistribuable spécial pour le shell isolé.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Conditions préalables pour la distribution d’Applications de Shell isolé  
  
|Nom|Description|  
|----------|-----------------|  
|SDK Visual Studio|Le Kit de développement logiciel vous devez disposer pour développer et tester des extensions de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Vous pouvez également utiliser le Kit de développement logiciel pour créer votre propre instance du shell isolé Visual Studio.<br /><br /> Visual Studio est un prérequis pour le Kit de développement.|  
|Microsoft Visual Studio isolé redistribuable du Shell|Shell isolé redistribuables que vous incluez dans votre programme d’installation lorsque vous générez un environnement d’outils dans Visual Studio. Le package redistribuable de Shell isolé inclut le .NET Framework 4.5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Création d’un programme d’Installation pour l’Application  
 Vous devez créer un programme d’installation spéciales pour votre application de shell intégré ou isolé. Pour plus d’informations, consultez [installation d’une Application de Shell isolé](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Autoriser les mises à jour à votre Application  
 Le programme d’installation doit tenir compte du fait que votre application sera être mis à jour, mises à jour Microsoft ou par les mises à jour de votre entreprise. Pour plus d’informations sur les mises à jour, consultez [maintenance des instructions pour les Applications de Shell isolé](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).
