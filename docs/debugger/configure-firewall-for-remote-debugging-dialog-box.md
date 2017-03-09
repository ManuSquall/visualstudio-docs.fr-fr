---
title: "Configurer le pare-feu pour le d&#233;bogage distant, bo&#238;te de dialogue | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.firewallconfiguration"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
helpviewer_keywords: 
  - "Configurer le pare-feu pour le débogage distant (boîte de dialogue)"
  - "débogage distant, configuration des pare-feu"
  - "pare-feu, configuration pour le débogage distant"
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Configurer le pare-feu pour le d&#233;bogage distant, bo&#238;te de dialogue
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette boîte de dialogue apparaît lorsque le Pare\-feu Windows empêche le débogueur de recevoir des informations via le réseau. Pour poursuivre le débogage distant, vous devez ouvrir une faille dans le pare\-feu pour que le débogueur puisse recevoir des informations.  
  
> [!CAUTION]
>  L'ouverture d'une faille dans le pare\-feu peut exposer votre ordinateur à des menaces de sécurité que le pare\-feu est censé bloquer. L’ouverture d’une faille pour le débogage à distance débloque les ports 4020 et 4021 dans Visual Studio 2015. Dans d’autres versions de Visual Studio, des numéros de port différents sont utilisés. Pour plus d'informations, consultez [Affectations de port du débogueur distant](../debugger/remote-debugger-port-assignments.md). De plus, il permet au débogueur d'ouvrir des ports supplémentaires. Pour plus d'informations, consultez [Configurer le Pare\-feu Windows pour le débogage distant](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## Liste UIElement  
 **Annuler le débogage distant**  
 Annule la tentative de débogage distant. Les paramètres de sécurité de votre ordinateur restent intacts.  
  
 **Débloquer le débogage distant à partir des ordinateurs sur le réseau local \(sous\-réseau\)**  
 Active le débogage distant d'ordinateurs sur votre sous\-réseau local. Cela peut rendre vulnérables les ordinateurs sur votre sous\-réseau local, mais le pare\-feu continue à bloquer des informations provenant de l'extérieur du sous\-réseau.  
  
 **Débloquer le débogage distant à partir de tous les ordinateurs**  
 Active le débogage distant d'ordinateurs n'importe où sur le réseau. Ce paramètre est le moins sécurisé.  
  
## Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Configurer les outils de contrôle à distance sur le périphérique](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)   
 [Référence du débogage de l'interface utilisateur](../debugger/debugging-user-interface-reference.md)