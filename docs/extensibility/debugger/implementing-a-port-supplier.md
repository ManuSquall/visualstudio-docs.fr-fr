---
title: "L&#39;impl&#233;mentation d&#39;un fournisseur de Port | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage (débogage SDK), l'implémentation de fournisseurs de port"
  - "fournisseurs de port, l'implémentation"
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# L&#39;impl&#233;mentation d&#39;un fournisseur de Port
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

orifices d'alimentation d'un fournisseur de port sur demande au gestionnaire de débogage de session \(SDM\).  Un fournisseur de port doit être implémenté lors de le débogage à non\-DCOM un ordinateur ou lorsqu'un nouvel appareil doit être pris en charge.  Par exemple, pour fournir le débogage à un téléphone portable, vous pouvez implémenter un fournisseur de port qui fournit les ports qui se connectent au téléphone portable \(peut\-être à l'aide de IR ou d'une connexion de cellule\) et énumère les processus et programme s'exécutant sous windows phone.  
  
 Pour déboguer programme sur les ordinateurs Windows \(débogage distant\), Visual Studio fournit des fournisseurs de port pour les processus \(CLR\) du common langage runtime, il n'est donc pas besoin d'implémenter votre propre fournisseur de port dans ce cas.  
  
## Dans cette section  
 [L'implémentation et l'inscription d'un fournisseur de Port](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Explique comment le SDM interagit avec le fournisseur de port et ses ports.  
  
 [Interfaces de fournisseur de Port requis](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 documente les interfaces qui doivent être implémentées pour obtenir un fournisseur de port.  
  
## Rubriques connexes  
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)  
 décrit les concepts architecturaux de débogage principal.  
  
## Voir aussi  
 [Extensibilité du débogueur de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)