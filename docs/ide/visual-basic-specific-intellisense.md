---
title: "Options IntelliSense sp&#233;cifiques &#224; Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense (Visual Basic)"
  - "IntelliSense (Visual Studio), Visual Basic"
ms.assetid: 4dec8753-05e5-4f74-b304-5f8c4ed8723b
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Options IntelliSense sp&#233;cifiques &#224; Visual Basic
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'éditeur de code source de Visual Basic propose les fonctionnalités IntelliSense suivantes :  
  
-   Conseils syntaxiques  
  
     Les conseils syntaxiques affichent la syntaxe de l'instruction que vous tapez.  Ils sont utiles pour des instructions de type [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement).  
  
## Saisie semi\-automatique  
  
-   Saisie semi\-automatique de divers mots clés.  
  
     Par exemple, si vous tapez `goto` suivi d'un espace, IntelliSense affiche une liste des étiquettes définies dans un menu déroulant.  Les autres mots clés pris en charge sont `Exit`, `Implements`, `Option` et `Declare`.  
  
-   Saisie semi\-automatique pour les membres de type `Enum` et `Boolean`  
  
     Lorsqu'une instruction fait référence à un membre d'une énumération, IntelliSense affiche la liste des membres de type `Enum`.  Lorsqu'une instruction fait référence à un membre de type `Boolean`, IntelliSense affiche un menu déroulant contenant les valeurs True et False.  
  
 Pour désactiver par défaut la saisie semi\-automatique, désélectionnez l'option **Répertorier automatiquement les membres** dans la page de propriétés **Général** du dossier **Visual Basic**.  
  
 Vous pouvez appeler manuellement la saisie semi\-automatique en appelant les fonctionnalités Liste des membres, Compléter le mot ou ALT\+DROITE.  Pour plus d'informations, consultez [Utilisation de la fonctionnalité IntelliSense](../ide/using-intellisense.md).  
  
## IntelliSense par zone  
 IntelliSense par zone aide les développeurs Visual Basic qui doivent déployer leurs applications via [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] et sont contraints à des paramètres de confiance partielle.  Cette fonctionnalité :  
  
-   Permet de choisir les autorisations avec lesquelles l'application s'exécutera.  
  
-   Affiche les API dans la Zone choisie comme disponibles dans la liste des membres, et les API nécessitant des autorisations supplémentaires comme non disponibles.  
  
 Pour plus d'informations, consultez [Sécurité d'accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
## Voir aussi  
 [Utilisation de la fonctionnalité IntelliSense](../ide/using-intellisense.md)