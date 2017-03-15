---
title: "S&#233;curit&#233; et assemblys satellites localis&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "assemblys (Visual Studio), sécurité"
  - "signature du code, assemblys"
  - "paires de clés pour assemblys avec nom fort"
  - "localisation, assemblys satellites"
  - "assemblys satellites, localisé"
  - "sécurité (Visual Studio), assemblys"
  - "assemblys avec nom fort, localisé"
  - "assemblys avec nom fort, considérations relatives à la sécurité"
ms.assetid: 6d953840-b301-47d5-8d34-30c1b29b5071
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# S&#233;curit&#233; et assemblys satellites localis&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si votre assembly principal utilise des noms forts, les assemblys satellites doivent être signés à l'aide de la même clé privée que l'assembly principal.  Si la paire de clés publique\/privée de l'assembly principal ne correspond pas à celle de l'assembly satellite, vos ressources ne seront pas chargées.  Pour plus d'informations sur la signature d'assemblys, consultez [Comment : signer un assembly avec un nom fort](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md).  
  
 D'une manière générale, vous pouvez avoir besoin que le groupe de signature de votre organisation ou qu'une organisation de signature externe signe les assemblys à l'aide de la clé privée.  Cela est dû à la nature sensible de la clé privée : l'accès est souvent limité à une poignée d'individus.  Vous pouvez utiliser la signature différée pendant le développement.  Pour plus d'informations, consultez [Temporisation de signature d'un assembly](../Topic/Delay%20Signing%20an%20Assembly.md).  
  
## Voir aussi  
 [Aspects de la sécurité des assemblys](../Topic/Assembly%20Security%20Considerations.md)   
 [Concepts fondamentaux sur la sécurité](../Topic/Key%20Security%20Concepts.md)   
 [Introduction aux applications internationales basées sur le .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Localisation d'applications](../ide/localizing-applications.md)   
 [Globalisation et localisation d'applications](../ide/globalizing-and-localizing-applications.md)