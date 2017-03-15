---
title: "Comment&#160;: utiliser la fen&#234;tre Code Machine | Microsoft Docs"
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
  - "vs.debug.disassembly"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "langage assembleur, débogage de code assembleur inline"
  - "points d’arrêt, fenêtre Code machine"
  - "Code Machine (fenêtre)"
  - "code machine"
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: utiliser la fen&#234;tre Code Machine
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonctionnalité n'est disponible que si le débogage au niveau de l'adresse est activé dans la boîte de dialogue **Options**, nœud **Débogage**.  Elle n'est pas disponible pour le débogage de script ni le débogage SQL.  
  
 La fenêtre **Code Machine** affiche le code assembleur correspondant aux instructions créées par le compilateur.  Si vous déboguez du code managé, ces instructions assembleur correspondent au code natif créé par le compilateur juste\-à\-temps \(JIT\), et non au langage intermédiaire de Microsoft \(MSIL\) généré par le compilateur Visual Studio.  
  
 Outre les instructions assembleur, la fenêtre **Code Machine** peut afficher les informations facultatives suivantes :  
  
-   L'adresse mémoire de chaque instruction.  Pour les applications natives, il s'agit effectivement de l'adresse mémoire.  Pour Visual Basic, C\# ou le code managé, il s'agit d'un offset à partir du début de la fonction.  
  
-   Le code source dont est tiré le code assembleur.  
  
-   Octets du code \(représentation sous forme d'octets des instructions machine réelles ou MSIL\).  
  
-   Les noms des symboles pour les adresses mémoire.  
  
-   Les numéros de ligne correspondant au code source.  
  
 Les instructions en langage assembleur sont constituées de mnémoniques, qui sont des abréviations des noms d'instructions, et de symboles représentant des variables, des registres et des constantes.  Chaque instruction en langage machine est représentée par un mnémonique en langage assembleur, généralement suivi d'une ou plusieurs variables, registres ou constantes.  
  
 Si vous ne savez pas lire le langage assembleur et souhaitez pourtant profiter pleinement de la fenêtre Code Machine, consultez un ouvrage sur la programmation en langage assembleur.  La programmation en langage assembleur va bien au\-delà de l'objet de cette brève introduction sur la fenêtre Code Machine.  
  
 Dans la mesure où le code assembleur dépend beaucoup des registres du processeur ou, dans le cas du code managé, des registres du Common Language Runtime. Il est souvent plus judicieux d'utiliser la fenêtre Code Machine en même temps que la fenêtre Registres car cela vous permet d'examiner le contenu des registres.  
  
 Vous n'aurez probablement jamais le désir ni le besoin de consulter les instructions du code machine dans leur format numérique brut, plutôt qu'en langage assembleur.  Néanmoins, si vous le souhaitez, vous pouvez les consulter dans la fenêtre Mémoire ou en sélectionnant Octets du code dans le menu contextuel de la fenêtre Code Machine.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour afficher la fenêtre Code Machine  
  
-   Dans le menu **Déboguer**, sélectionnez **Fenêtres**, puis cliquez sur **Code machine**.  
  
     Le débogueur doit être en cours d'exécution ou en mode arrêt.  
  
### Pour activer ou désactiver les informations facultatives  
  
-   Cliquez avec le bouton droit dans la fenêtre **Code Machine**, puis activez ou désactivez les options souhaitées dans le menu contextuel.  
  
     Dans la marge de gauche, une flèche jaune marque l'emplacement du point d'exécution en cours.  Pour le code natif, il correspond au compteur programme de la CPU.  Cet emplacement montre l'instruction suivante qui sera exécutée dans votre programme.  
  
     Pour plus d'informations, consultez [Déplacement d'une page vers le haut ou vers le bas dans la mémoire](../debugger/how-to-page-up-or-down-in-memory.md).  
  
## Voir aussi  
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)   
 [Comment : utiliser la fenêtre Registres](../debugger/how-to-use-the-registers-window.md)