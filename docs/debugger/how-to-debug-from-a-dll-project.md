---
title: "Comment&#160;: d&#233;boguer &#224; partir d&#39;un projet DLL | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "déboguer (Visual Studio), DLL"
  - "déboguer des DLL"
  - "projets DLL, débogage"
  - "DLL, déboguer des projets"
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 30
---
# Comment&#160;: d&#233;boguer &#224; partir d&#39;un projet DLL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Pour démarrer le débogage d'un projet de DLL, vous devez spécifier l'application appelante dans les propriétés du projet.  Les pages de propriétés C\+\+ diffèrent dans la disposition et le contenu par rapport aux pages de propriétés C\# et Visual Basic.  
  
 Si une DLL managée est appelée par du code natif et que vous voulez déboguer les deux, vous pouvez le spécifier dans les propriétés du projet.  Pour plus d'informations, consultez [Comment : déboguer en mode mixte](../debugger/how-to-debug-in-mixed-mode.md).  
  
> [!NOTE]
>  Vous ne pouvez pas spécifier une application appelante externe dans les éditions Express de Visual Studio.  Au lieu de cela, vous devez ajouter un projet exécutable à la solution, le définir comme projet de démarrage et appeler les méthodes de votre DLL depuis le projet exécutable.  
  
### Pour spécifier l'application appelante dans un projet C\+\+  
  
1.  Cliquez avec le bouton droit sur le nœud du projet dans l'**Explorateur de solutions**, puis sélectionnez **Propriétés**.  Accédez à l'onglet **Débogage**.  
  
2.  Assurez\-vous que le champ **Configuration** en haut de la fenêtre est défini sur **Débogage**.  
  
3.  Accédez à **Propriétés de configuration \/ Débogage**.  
  
4.  Dans la liste **Débogueur à lancer**, choisissez **Débogueur Windows local** ou **Débogueur Windows distant**.  
  
5.  Dans la zone **Commande** ou **Commande distante**, ajoutez le nom du chemin d'accès complet de l'application.  
  
6.  Ajoutez les arguments nécessaires du programme à la zone **Arguments de la commande**.  
  
### Pour spécifier l'application appelante dans un projet C\# ou Visual basic  
  
1.  Cliquez avec le bouton droit sur le nœud du projet dans l'**Explorateur de solutions**, puis sélectionnez **Propriétés**.  Accédez à l'onglet **Débogage**.  
  
     Sélectionnez **Démarrer le programme externe** et ajoutez le nom du chemin d'accès complet du programme à exécuter.  
  
     Si vous devez ajouter les arguments de ligne de commande du programme externe, ajoutez\-les dans le champ **Arguments de la ligne de commande**.  
  
2.  Vous pouvez également appeler une application via une URL.  \(Vous pouvez procéder ainsi si vous déboguez une DLL managée utilisée par une application ASP.NET locale.\)  
  
     Sous **Action de démarrage**, sélectionnez la case d'option **Démarrer le navigateur avec l'URL :** et entrez l'URL.  
  
### Pour démarrer le débogage à partir du projet de DLL  
  
1.  Définissez des points d'arrêt selon vos besoins.  
  
2.  Démarrez le débogage \(appuyez sur F5, cliquez sur la flèche verte ou cliquez sur **Déboguer \/ Démarrer le débogage**\).  
  
## Voir aussi  
 [Débogage de projets DLL](../debugger/debugging-dll-projects.md)   
 [Paramètres de projet pour des configurations Debug C\#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Paramètres de projet pour une configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Paramètres de projet pour une configuration Debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)