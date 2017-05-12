---
title: "Comment&#160;: r&#233;activer un compl&#233;ment VSTO qui a &#233;t&#233; d&#233;sactiv&#233;"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.Warning.DisabledAddIn"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "compléments désactivés"
  - "compléments (développement Office dans Visual Studio), désactivés"
  - "compléments (développement Office dans Visual Studio), activation"
ms.assetid: 69719a0a-984c-42cd-80a2-1367c866e5df
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Comment&#160;: r&#233;activer un compl&#233;ment VSTO qui a &#233;t&#233; d&#233;sactiv&#233;
  Les applications Microsoft Office peuvent désactiver les compléments VSTO qui se comportent de façon inattendue. Si une application ne charge pas votre complément VSTO quand vous essayez de la déboguer, cela peut\-être dû au fait qu'elle a désactivé votre complément VSTO de manière forcée ou en douceur.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## Compléments VSTO désactivés de manière forcée  
 La désactivation de manière forcée peut se produire quand un complément VSTO entraîne la fermeture inattendue de l'application. Elle peut également se produire sur votre ordinateur de développement si vous arrêtez le débogueur pendant que le gestionnaire d'événements <xref:Microsoft.Office.Tools.AddIn.Startup> de votre complément VSTO est en cours d'exécution.  
  
#### Pour réactiver un complément VSTO  
  
1.  Dans l'application, cliquez sur l'onglet **Fichier**.  
  
2.  Cliquez sur le bouton **Options de** *nom\_application*.  
  
3.  Dans le volet des catégories, cliquez sur **Compléments**.  
  
4.  Dans le volet d'informations, vérifiez que le complément VSTO apparaît dans la liste **Compléments d'applications désactivés**.  
  
     La colonne **Nom** indique le nom de l'assembly, et la colonne **Emplacement** indique le chemin d'accès complet du manifeste de l'application.  
  
5.  Dans la zone **Gérer**, cliquez sur **Éléments désactivés**, puis sur **Atteindre**.  
  
6.  Sélectionnez le complément VSTO, puis cliquez sur **Activer**.  
  
7.  Cliquez sur **Fermer**.  
  
## Compléments VSTO désactivés en douceur  
 La désactivation en douceur peut se produire quand un complément VSTO génère une erreur qui n'entraîne pas la fermeture inattendue de l'application. Par exemple, une application peut entraîner la désactivation en douceur d'un complément VSTO, si ce dernier lève une exception non gérée pendant l'exécution du gestionnaire d'événements <xref:Microsoft.Office.Tools.AddIn.Startup>.  
  
> [!NOTE]  
>  Quand vous réactivez un complément VSTO désactivé en douceur, l'application essaie immédiatement de charger le complément VSTO. Si le problème qui a obligé initialement l'application à désactiver en douceur le complément VSTO n'a pas été résolu, l'application désactivera à nouveau en douceur le complément VSTO.  
  
#### Pour réactiver un complément VSTO  
  
1.  Dans l'application, cliquez sur l'onglet **Fichier**.  
  
2.  Cliquez sur le bouton **Options de** *nom\_application*.  
  
3.  Dans le volet des catégories, cliquez sur **Compléments**.  
  
4.  Dans le volet d'informations, vérifiez que le complément VSTO apparaît dans la liste **Compléments d'applications inactifs**.  
  
     La colonne **Nom** indique le nom de l'assembly, et la colonne **Emplacement** indique le chemin d'accès complet du manifeste de l'application.  
  
5.  Dans la zone **Gérer**, cliquez sur **Compléments COM**, puis sur **Atteindre**.  
  
6.  Dans la boîte de dialogue **Compléments COM**, cochez la case en regard du complément VSTO désactivé.  
  
7.  Cliquez sur **OK**.  
  
## Voir aussi  
 [Génération de solutions Office](../vsto/building-office-solutions.md)   
 [Débogage de projets Office](../vsto/debugging-office-projects.md)   
 [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md)  
  
  