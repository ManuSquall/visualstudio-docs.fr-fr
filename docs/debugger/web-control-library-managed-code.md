---
title: "Biblioth&#232;que de contr&#244;les Web (code manag&#233;) | Microsoft Docs"
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
  - "déboguer (Visual Studio), bibliothèques de contrôles Web"
  - "déboguer des DLL"
ms.assetid: 2413883f-9e88-406d-b874-0ed743b75d40
caps.latest.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 26
---
# Biblioth&#232;que de contr&#244;les Web (code manag&#233;)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le modèle de projet de bibliothèque de contrôles Web permet de créer une DLL.  Étant donné que la bibliothèque de classes est une DLL, vous ne pouvez pas l'exécuter directement.  Vous devez créer une page [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] qui incorpore le contrôle.  Pour plus d'informations, consultez [Web Control Library Template](http://msdn.microsoft.com/fr-fr/00666b07-71d2-4ace-a13c-cc130a3ce372).  
  
### Pour déboguer une bibliothèque de contrôles Web \(Méthode 1\)  
  
1.  Ouvrez un projet de bibliothèque de contrôles Web existant ou créez\-en un.  
  
2.  Créez une page [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] qui incorpore le contrôle.  
  
3.  Sur le site Web qui héberge l'atelier de test [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], créez un sous\-répertoire appelé `/Code`.  
  
4.  Copiez le code source du contrôle dans le sous\-répertoire `/Code`.  
  
5.  Ouvrez le code source dans le sous\-répertoire `/Code` et définissez des points d'arrêt.  
  
6.  Ouvrez une fenêtre de navigateur avec une URL qui pointe sur l'atelier de test.  Vous pouvez commencer à déboguer dès qu'un point d'arrêt dans le contrôle est atteint.  
  
### Pour déboguer une bibliothèque de contrôles Web \(Méthode 2\)  
  
1.  Créez le projet d'application hôte et le projet de contrôle Web dans la même solution.  
  
2.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur l'application hôte et sélectionnez **Ajouter une référence**.  
  
3.  Ajoutez une référence au projet de contrôle Web.  
  
## Voir aussi  
 [Applications Web ASP.NET](../debugger/debugging-preparation-aspnet-web-applications.md)