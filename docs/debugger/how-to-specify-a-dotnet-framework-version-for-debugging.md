---
title: "Comment&#160;: sp&#233;cifier une version .NET Framework pour le d&#233;bogage | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
helpviewer_keywords: 
  - ".NET Framework, spécifier une version pour le débogage"
  - "déboguer (Visual Studio), spécifier la version du .NET Framework"
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: sp&#233;cifier une version .NET Framework pour le d&#233;bogage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le débogueur [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] prend en charge le débogage des versions antérieures ainsi que de la version actuelle de Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Si vous démarrez une application à partir de Visual Studio, le débogueur identifie toujours la version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] appropriée pour l'application que vous déboguez.  Si l'application est déjà exécutée et que vous utilisez l'option **Attacher à**, il se peut que le débogueur ne puisse pas toujours identifier une version antérieure de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Si cela se produit, un message d'erreur s'affiche qui indique,  
  
 Le débogueur a évalué de façon incorrecte la version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que votre application va utiliser.  
  
 Dans ces cas rares, vous pouvez définir une clé de Registre pour indiquer au débogueur la version à utiliser.  
  
### Pour spécifier une version .NET Framework pour le débogage  
  
1.  Recherchez dans le répertoire Windows\\Microsoft.NET\\Framework les versions du .NET Framework installées sur votre ordinateur.  Les numéros de version sont similaires à ceci :  
  
     `V1.1.4322`  
  
     Identifiez le numéro de version correct et prenez\-en note.  
  
2.  Démarrez l'**Éditeur du Registre** \(regedit\).  
  
3.  Dans l'**Éditeur du Registre**, ouvrez le dossier HKEY\_LOCAL\_MACHINE.  
  
4.  Accédez à : HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\10.0\\AD7Metrics\\Engine\\{449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B}  
  
     Si la clé n'existe pas, cliquez avec le bouton droit sur HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\10.0\\AD7Metrics\\Engine, puis cliquez sur **Nouvelle clé**.  Nommez la nouvelle clé `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5.  Après avoir navigué à {449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B}, recherchez dans la colonne **Nom** la clé CLRVersionForDebugging.  
  
    1.  Si la clé n'existe pas, cliquez avec le bouton droit sur {449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B}, puis cliquez sur **Nouvelle valeur de chaîne**.  Cliquez ensuite avec le bouton droit sur la nouvelle valeur de chaîne, puis cliquez sur **Renommer** et tapez `CLRVersionForDebugging`.  
  
6.  Double\-cliquez sur **CLRVersionForDebugging**.  
  
7.  Dans la zone **Modification de la chaîne**, tapez le numéro de version du .NET Framework dans la zone **Valeur**.  Par exemple : V1.1.4322  
  
8.  Cliquez sur **OK**.  
  
9. Fermez l'**Éditeur du Registre**.  
  
     Si vous obtenez encore un message d'erreur lorsque vous commencez à déboguer, vérifiez que vous avez entré correctement le numéro de version dans le Registre.  Assurez\-vous également que la version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que vous utilisez est prise en charge par Visual Studio.  Le débogueur est compatible avec la version actuelle et les versions antérieures du .NET Framework, mais il n'offre peut\-être pas une compatibilité ascendante avec les futures versions.  
  
## Voir aussi  
 [Paramètres et préparation du débogage](../debugger/debugger-settings-and-preparation.md)