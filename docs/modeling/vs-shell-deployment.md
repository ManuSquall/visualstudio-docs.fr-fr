---
title: "D&#233;ploiement du shell VS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 2
---
# D&#233;ploiement du shell VS
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un l'interpréteur de commandes isolé vous permet de déterminer dont les fonctionnalités de Visual Studio vous avez besoin pour interagir avec votre langage spécifique au domaine et comment cette solution doit apparaître.  Pour plus d'informations sur Visual Studio l'interpréteur de commandes isolé, consultez [Personnalisation de l’interpréteur de commandes isolé](../extensibility/customizing-the-isolated-shell.md).  Vous trouverez plus d'informations sur la personnalisation du shell isolé dans [Customizing the Isolated Shell](http://msdn.microsoft.com/fr-fr/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### Pour définir un shell Visual Studio comme cible de déploiement  
  
1.  dans le projet d' **DslPackage** , ouvrez **source.extension.tt**.  
  
2.  sous l'insertion d' `<SupportedProducts>` :  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Remplacez *MyIsolatedShell* par le nom de votre package d'isolement du shell.