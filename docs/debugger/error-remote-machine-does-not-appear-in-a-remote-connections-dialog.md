---
title: "Erreur&#160;: l’ordinateur distant n’appara&#238;t pas dans une bo&#238;te de dialogue Connexions &#224; distance | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 5fd98a5b-2cf3-4438-8b0f-6f1a742a62ce
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erreur&#160;: l’ordinateur distant n’appara&#238;t pas dans une bo&#238;te de dialogue Connexions &#224; distance
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si l’ordinateur distant n’apparaît pas dans la boîte de dialogue Connexions à distance, vérifiez les causes courantes suivantes.  
  
 Si vous utilisez le mode de compatibilité managé, consultez la documentation de Visual Studio 2010 : [Dépannage du débogage distant \- Visual Studio 2010](https://msdn.microsoft.com/en-us/library/2ys11ead\(v=vs.100\).aspx) .  
  
### Causes courantes de cette erreur  
  
-   L’ordinateur distant s’exécute sur un ordinateur qui se trouve dans un sous\-réseau différent. Pour résoudre ce problème, tapez manuellement le nom ou l’adresse IP de l’ordinateur dans la boîte de dialogue Qualificateur  
  
-   Le débogueur distant ne fonctionne pas sur l’ordinateur distant. Pour résoudre ce problème, démarrez le débogueur distant.  
  
-   Le pare\-feu bloque les communications entre Visual Studio et l’ordinateur distant. Pour résoudre ce problème, configurez votre pare\-feu pour permettre à Visual Studio et au débogueur distant \(msvsmon\) de communiquer.  
  
-   Un logiciel antivirus bloque les communications entre Visual Studio et l’ordinateur distant. Pour résoudre ce problème, configurez le logiciel antivirus pour permettre à Visual Studio et au débogueur distant \(msvsmon\) de communiquer.  
  
## Voir aussi  
 [Configurer les outils de contrôle à distance sur le périphérique](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)