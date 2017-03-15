---
title: "Comment&#160;: examiner du code syst&#232;me apr&#232;s une exception | Microsoft Docs"
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
  - "débogage, exceptions"
  - "exceptions, débogage"
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Comment&#160;: examiner du code syst&#232;me apr&#232;s une exception
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsqu'une exception est levée, il peut s'avérer nécessaire d'examiner le code dans un appel système afin de déterminer la cause de l'exception.  Pour ce faire, suivez la procédure ci\-dessous si aucun symbole n'est chargé pour le code système ou si l'option Uniquement mon code est activée.  
  
### Pour examiner du code système après une exception  
  
1.  Cliquez avec le bouton droit sur la fenêtre **Pile des appels**, puis cliquez sur **Afficher le code externe** dans le menu contextuel.  
  
     Si l'option Uniquement mon code n'est pas activée, cette option n'est pas disponible dans le menu contextuel et le code système s'affiche par défaut.  
  
2.  Cliquez avec le bouton droit sur les frames de code externe qui s'affichent à présent dans la fenêtre **Pile des appels**.  
  
3.  Pointez sur **Charger les symboles depuis** et cliquez sur **Serveur de symboles publics Microsoft**.  
  
    1.  Si l'option Uniquement mon code était activée, une boîte de dialogue s'affiche  pour indiquer que cette option est à présent désactivée,  ce qui est nécessaire pour effectuer un pas à pas détaillé dans les appels système.  
  
    2.  La boîte de dialogue **Téléchargement des symboles publics** apparaît.  puis se ferme une fois le téléchargement terminé.  
  
4.  Vous pouvez à présent examiner le code système dans la fenêtre **Pile des appels** et dans d'autres fenêtres.  Par exemple, vous pouvez double\-cliquer sur une frame de pile d'appels pour afficher le code dans une fenêtre **Code Machine** ou source.  
  
## Voir aussi  
 [Gestion des exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md)