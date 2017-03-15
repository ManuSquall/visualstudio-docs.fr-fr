---
title: "Avertissement de s&#233;curit&#233;&#160;: Le d&#233;bogueur doit ex&#233;cuter cette commande non approuv&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.sourceserver.securityalert"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Avertissement de s&#233;curit&#233;&#160;: Le d&#233;bogueur doit ex&#233;cuter cette commande non approuv&#233;e
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette boîte de dialogue d'avertissement apparaît lorsque vous utilisez le serveur source.  Elle indique que la commande que le débogueur a besoin d'exécuter pour obtenir le code source n'est pas dans la liste de commandes de confiance pour le serveur source contenue dans le fichier srcsvr.ini.  Si c'est une commande valide, vous pouvez l'ajouter au fichier srcsvr.ini.  Sinon, vous ne devez pas l'exécuter.  Pour plus d'informations, consultez [Spécifier les fichiers de symbole \(.pdb\) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## Texte du message  
 Le débogueur doit exécuter cette commande non approuvée pour obtenir le code source du serveur source.  
  
 Si le fichier de symboles de débogage \(\*.pdb\) ne provient pas d'une source connue et approuvée, cette commande peut être non valide ou dangereuse à exécuter.  
  
 Souhaitez\-vous exécuter cette commande ?  
  
## Liste UIElement  
 Zone de texte  
 Commande du fichier .pdb à exécuter.  
  
 Run  
 Permet l'exécution de la commande.  
  
 Ne pas exécuter  
 Arrête l'exécution de la commande et le téléchargement du fichier à partir du serveur source.  
  
## Voir aussi  
 [Spécifier les fichiers de symbole \(.pdb\) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Serveur source](http://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).asp)