---
title: "Ces configurations de projet sont obsol&#232;tes&#160;: &lt;configuration&gt;. Voulez-vous les g&#233;n&#233;rer&#160;? | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Message.BuildOutOfDateProjects"
ms.assetid: d0711f3b-3a2e-4247-afad-9e6468f9df96
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ces configurations de projet sont obsol&#232;tes&#160;: &lt;configuration&gt;. Voulez-vous les g&#233;n&#233;rer&#160;?
Vous êtes en train de modifier un projet Visual Studio ou vous avez sélectionné un projet dans l’Explorateur de solutions, et vous choisissez de démarrer le projet \(F5\) ou de l’exécuter sans débogage \(CTRL\+F5\). Un ou plusieurs projets autorisent le débogage sans régénération, même si le projet a été modifié à partir de la dernière build.  
  
 L’environnement de développement intégré \(IDE\) demande s’il est possible ou non de régénérer des projets qui autorisent le débogage sans régénération.  
  
### Pour répondre à ce message  
  
-   Sélectionnez l’un des boutons situés dans la partie inférieure du message. Les options sont les suivantes :  
  
|Terme|Définition|  
|-----------|----------------|  
|**Oui**|Les projets obsolètes sont régénérés. Signification :<br /><br /> -   Le projet est généré s’il ne l’a pas encore été.<br />-   Si le projet a été modifié depuis la dernière build, il est régénéré.<br />-   Le projet est débogué ou démarré sans débogage.|  
|**Non**|Ne sont régénérés que les projets obsolètes qui doivent l’être avant le débogage. Signification :<br /><br /> -   Si le projet autorise le débogage sans régénération \(par exemple, un projet Application MFC Visual C\+\+\), le projet n’est pas régénéré.<br />-   Si le projet doit être régénéré avant le débogage \(par exemple, un projet Visual Basic\), il est régénéré.<br />-   Le projet est débogué ou démarré sans débogage.|  
|**Annuler**|L’opération actuelle est arrêtée. Aucun projet n’est généré, exécuté ou débogué.|  
  
## Voir aussi  
 [Boîte de dialogue Gestionnaire de configuration](http://msdn.microsoft.com/fr-fr/fa182dca-282e-4ae5-bf37-e155344ca18b)   
 [Comment : créer des configurations de génération de solution et de projet](../Topic/How%20to:%20Create%20Solution%20and%20Project%20Build%20Configurations.md)   
 [Comment : créer et supprimer les dépendances d'un projet](../Topic/How%20to:%20Create%20and%20Remove%20Project%20Dependencies.md)   
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/fr-fr/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Project Dependencies, Common Properties, Solution Property Pages Dialog Box](http://msdn.microsoft.com/fr-fr/2ba638fc-719c-4a79-b166-3455a4374e31)   
 [Génération d'applications dans Visual Studio](../ide/compiling-and-building-in-visual-studio.md)   
 [Présentation des configurations de build](../ide/understanding-build-configurations.md)   
 [NIB : projets comme conteneurs](http://msdn.microsoft.com/fr-fr/87d40f63-f487-4767-8963-64beec27ba1b)   
 [NIB : Gestion des éléments dans les projets](http://msdn.microsoft.com/fr-fr/762e606b-7f44-4b66-97a1-e30a703654a0)