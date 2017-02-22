---
title: "Erreur&#160;: Assurez-vous que DNS est correctement configur&#233; sur l&#39;ordinateur cible | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.callback_dns_failed"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 2d364caf-73af-4186-bf9b-af186331cbe8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Erreur&#160;: Assurez-vous que DNS est correctement configur&#233; sur l&#39;ordinateur cible
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si vous essayez d'effectuer un débogage distant, vous risquez de recevoir ce message d'erreur :  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Cette erreur se produit lorsque l'ordinateur cible ne peut pas résoudre le nom de l'ordinateur hôte du débogueur Visual Studio.  Vérifiez les paramètres DNS sur l'ordinateur cible.  
  
-   Pour plus d'informations sur l'affichage de votre paramètre de DNS dans Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 ou Windows Server 2008 R2, procédez comme suit : sur le **Démarrer** menu, choisissez **Aide et support**, puis recherchez « Changer les paramètres TCP\/IP ».  
  
-   Pour plus d'informations, accédez au [site web Microsoft Windows](http://go.microsoft.com/fwlink/?LinkId=252720) et recherchez « Changer les paramètres TCP\/IP ».  
  
 Si vous ne pouvez pas résoudre le problème DNS, vous pouvez essayer d'exécuter le débogueur distant sous un compte différent.  Cette erreur se produit uniquement lorsque vous exécutez le débogueur distant sous le compte système local ou le compte de service réseau.  Si vous exécutez le débogueur distant sous un autre compte, il peut utiliser l'authentification NTLM, qui ne nécessite pas de DNS.  .  Pour la procédure, consultez [Erreur : Le service Débogueur distant Visual Studio sur l'ordinateur cible ne peut pas se reconnecter à cet ordinateur](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).