---
title: "Distribution d&#39;Applications de Shell isol&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Distribution d&#39;Applications de Shell isol&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous devez installer Visual Studio et le Kit de développement logiciel Visual Studio afin de créer une application de shell isolé. Pour distribuer l'application sur les ordinateurs d'autres utilisateurs ou des clients, vous devez inclure un package redistribuable spéciale pour le shell isolé.  
  
## Configuration requise pour distribuer des Applications du Shell isolé  
  
|Nom|Description|  
|---------|-----------------|  
|Kit de développement logiciel Visual Studio|Le Kit de développement logiciel vous devez disposer pour développer et tester des extensions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Vous pouvez également utiliser le Kit de développement logiciel pour créer votre propre instance de l'interpréteur de commandes de Visual Studio isolé.<br /><br /> Visual Studio est requise pour le Kit de développement logiciel.|  
|Microsoft Visual Studio isolé redistribuable du Shell|Shell isolé du redistribuable que vous incluez dans votre programme d'installation lorsque vous créez un environnement d'outils dans Visual Studio. Le package redistribuable Shell isolé inclut le .NET Framework 4.5.|  
  
## Création d'un programme d'Installation de l'Application  
 Vous devez créer un programme d'installation spéciales pour votre application d'environnement intégrée ou isolé. Pour plus d'informations, consultez [Installation d'une Application de Shell isolé](../extensibility/installing-an-isolated-shell-application.md).  
  
## Autoriser les mises à jour à votre Application  
 Le programme d'installation doit autoriser la possibilité que votre application sera être mis à jour, mises à jour ou mises à jour de votre entreprise. Pour plus d'informations sur les mises à jour, consultez la page [Instructions de maintenance pour les Applications de Shell isolé](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).