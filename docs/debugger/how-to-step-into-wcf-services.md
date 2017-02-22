---
title: "Comment&#160;: effectuer un pas &#224; pas d&#233;taill&#233; dans les services WCF | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
helpviewer_keywords: 
  - "débogage, WCF"
  - "WCF, débogage"
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Comment&#160;: effectuer un pas &#224; pas d&#233;taill&#233; dans les services WCF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], vous pouvez effectuer un pas à pas détaillé dans un service WCF.  Si le service WCF est dans la même solution [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que le client, vous pouvez atteindre des points d'arrêt à l'intérieur du service WCF.  
  
 Pour que le pas à pas détaillé fonctionne, le débogage doit être activé dans le fichier app.config ou web.config.  Pour plus d'informations sur le mode d'activation du débogage et pour les limitations du pas à pas détaillé dans les services WCF, consultez [Limitations du débogage WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### Pour effectuer un pas à pas détaillé dans un service WCF  
  
1.  Créez une solution [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui contient à la fois le client WCF et les projets de service WCF.  
  
2.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet de client WCF, puis cliquez sur **Définir comme projet de démarrage**.  
  
3.  Activez le débogage dans le fichier app.config ou web.config.  Pour plus d'informations, consultez [Limitations du débogage WCF](../debugger/limitations-on-wcf-debugging.md).  
  
4.  Dans le projet client, définissez un point d'arrêt à l'emplacement où vous souhaitez démarrer le pas à pas détaillé.  En règle générale, cet emplacement précède directement l'appel de service WCF.  
  
5.  Lancez l'exécution jusqu'au point d'arrêt, puis démarrez le pas à pas détaillé.  Le débogueur effectue automatiquement un pas à pas détaillé dans le service.  
  
## Voir aussi  
 [Débogage de services WCF](../debugger/debugging-wcf-services.md)   
 [Limitations du débogage WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Comment : déboguer un service WCF auto\-hébergé](../debugger/how-to-debug-a-self-hosted-wcf-service.md)