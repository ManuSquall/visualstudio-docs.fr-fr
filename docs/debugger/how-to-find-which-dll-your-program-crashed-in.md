---
title: "Comment&#160;: savoir quelle DLL a caus&#233; l&#39;arr&#234;t de votre programme | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.dll"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "débogueur, pannes de DLL"
  - "déboguer (Visual Studio), pannes de DLL"
  - "DLL, ordre de chargement de"
  - "erreurs (débogueur), pannes de DLL"
  - "Liste des modules (boîte de dialogue)"
  - "Modules (fenêtre)"
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Comment&#160;: savoir quelle DLL a caus&#233; l&#39;arr&#234;t de votre programme
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Si votre application tombe en panne pendant un appel à une DLL système ou au code de quelqu'un d'autre, vous devez rechercher la DLL active au moment de l'incident.  Si une panne survient dans une DLL en dehors de votre programme, vous pouvez identifier l'emplacement en utilisant la fenêtre **Modules**.  
  
### Pour savoir où une panne s'est produite à l'aide de la fenêtre Modules  
  
1.  Notez l'adresse où la panne s'est produite.  
  
2.  Dans le menu **Déboguer**, sélectionnez **Fenêtres**, puis cliquez sur **Modules**.  
  
3.  Dans la fenêtre **Modules**, trouvez la colonne **Adresse**.  Faites défiler la fenêtre à l'aide de la barre de défilement, si nécessaire.  
  
4.  Cliquez sur le bouton **Adresse** \(situé en haut de la colonne\) pour trier les DLL par adresse.  
  
5.  Recherchez dans la liste triée la DLL dont la plage d'adresse contient l'emplacement de la panne.  
  
6.  Les colonnes **Nom** et **Chemin d'accès** vous indiquent le nom et le chemin de la DLL.  
  
## Voir aussi  
 [Comment : déboguer des DLL natives](../Topic/How%20to:%20Debug%20Native%20DLLs.md)   
 [Comment : utiliser la fenêtre Modules](../debugger/how-to-use-the-modules-window.md)