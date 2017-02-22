---
title: "Afficher le navigateur Web, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "view.showwebbrowser"
helpviewer_keywords: 
  - "ShowWebBrowser (commande)"
  - "View.ShowWebBrowser (commande)"
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Afficher le navigateur Web, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Affiche l'URL spécifiée dans une fenêtre de navigateur Web au sein de l'environnement de développement intégré \(IDE\) ou en dehors de l'IDE.  
  
## Syntaxe  
  
```  
View.ShowWebBrowser URL [/new][/ext]  
```  
  
## Arguments  
 `URL`  
 Obligatoire.  URL du site Web.  
  
## Commutateurs  
 \/new  
 Facultatif.  Spécifie que la page doit s'afficher pour une nouvelle instance du navigateur Web.  
  
 \/ext  
 Facultatif.  Spécifie que la page doit s'afficher dans le navigateur Web par défaut en dehors de l'environnement de développement intégré \(IDE, Integrated Development Environment\).  
  
## Notes  
 L'alias de la commande **ShowWebBrowser** est **navigate** ou **nav**.  
  
## Exemple  
 L'exemple suivant affiche la page d'accueil de MSDN Online dans un navigateur Web en dehors de l'environnement de développement intégré.  Si une instance du navigateur Web est déjà ouverte, elle est utilisée ; sinon, une nouvelle instance est démarrée.  
  
```  
>View.ShowWebBrowser http://msdn.microsoft.com /ext  
```  
  
## Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)