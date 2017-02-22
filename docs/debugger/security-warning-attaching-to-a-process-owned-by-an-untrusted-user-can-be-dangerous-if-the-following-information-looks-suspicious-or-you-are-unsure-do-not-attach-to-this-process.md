---
title: "Avertissement de s&#233;curit&#233;&#160;: L&#39;attachement &#224; un processus appartenant &#224; un utilisateur non fiable peut &#234;tre dangereux. Si les informations suivantes semblent suspectes ou en cas de doutes, n&#39;attachez pas ce processus. | Microsoft Docs"
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
  - "vs.debug.attachsecuritywarning"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Avertissement de s&#233;curit&#233;&#160;: L&#39;attachement &#224; un processus appartenant &#224; un utilisateur non fiable peut &#234;tre dangereux. Si les informations suivantes semblent suspectes ou en cas de doutes, n&#39;attachez pas ce processus.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette boîte de dialogue d'avertissement s'affiche lorsque vous effectuez un attachement à un processus qui contient un code de niveau de confiance partiel ou qui appartient à un utilisateur non fiable, juste avant l'attachement.  Un processus non fiable qui contient un code malveillant a la possibilité d'endommager l'ordinateur qui effectue le débogage.  Si vous avez des raisons de vous méfier du processus, cliquez sur **Annuler** pour empêcher le débogage.  
  
 Pour supprimer cet avertissement lors du débogage d'un scénario légitime, fermez Visual Studio, puis définissez la valeur de cette clé de registre à 1 : `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`, puis redémarrez Visual Studio.  Après avoir terminé le débogage du scénario, réinitialisez la valeur à 0, et redémarrez Visual Studio.  
  
 Outre vous\-même, les « utilisateurs de confiance » comprennent un ensemble d'utilisateurs standard qui sont généralement définis sur des ordinateurs sur lesquels le .NET Framework est installé, comme `aspnet`, `localsystem`, `networkservice` et `localservice`.  
  
## Liste UIElement  
 Nom  
 Nom de l'assembly à déboguer  
  
 Utilisateur  
 Utilisateur actuel  
  
 Attacher  
 Cliquez pour poursuivre le débogage après attachement  
  
 Ne pas attacher  
 Ne pas attacher au processus  
  
## Voir aussi  
 [Attacher aux processus en cours d'exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)