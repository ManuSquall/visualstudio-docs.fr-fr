---
title: "Meilleures pratiques pour l&#39;utilisation des extraits de code | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "extraits de code, meilleures pratiques"
  - "extraits de code, sécurité"
ms.assetid: a293ec17-4dd7-4a99-8eeb-99f44a822a8b
caps.latest.revision: 22
caps.handback.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Meilleures pratiques pour l&#39;utilisation des extraits de code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le code dans un extrait de code affiche uniquement la manière la plus simple d'effectuer une action.  Pour la plupart des applications, le code doit être modifié en fonction de l'application.  
  
## Gestion des exceptions  
 En général, Catch et lever de nouveau de blocs try\-catch d'extrait de code… toutes les exceptions.  Il se peut que cela ne soit pas le bon choix pour votre projet.  Pour chaque exception, il existe plusieurs façons de répondre.  Pour obtenir des exemples, consultez [Comment : gérer une exception à l'aide de try\/catch](../Topic/How%20to:%20Handle%20an%20Exception%20Using%20try-catch%20\(C%23%20Programming%20Guide\).md) et [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).  
  
## Emplacements des fichiers  
 Lorsque vous adaptez les emplacements de fichiers à votre application, vous devez considérer ce qui suit :  
  
-   Trouver un emplacement accessible.  Les utilisateurs ne peuvent pas avoir accès au dossier program files de l'ordinateur, donc stocker les fichiers avec les fichiers d'application peut ne pas s'exécuter.  
  
-   Trouver un emplacement sécurisé.  Le stockage des fichiers dans le dossier racine \(C:\\\) n'est pas sécurisé.  Pour les données d'application, nous vous recommandons d'utiliser le dossier \\Application Data.  Pour les données utilisateur, l'application peut créer un fichier pour chaque utilisateur dans le dossier \\Mes documents.  
  
-   Utiliser un nom de fichier valide.  Vous pouvez utiliser les contrôles d' <xref:System.Windows.Forms.OpenFileDialog> et d' <xref:System.Windows.Forms.SaveFileDialog> pour réduire la probabilité des noms de fichiers valides.  Gardez à l'esprit qu'entre le moment où l'utilisateur sélectionne un fichier et le moment où votre code manipule le fichier, il se peut que le fichier ait été supprimé.  En outre, l'utilisateur ne dispose peut\-être pas des autorisations pour écrire dans le fichier.  
  
## Sécurité  
 Le niveau de sécurité d'un extrait de code dépend de l'emplacement où il est utilisé dans le code source et de la façon dont il est modifié après avoir été inséré dans le code.  La liste suivante contient quelques\-unes des zones qui doivent faire l'objet d'une attention particulière :  
  
-   Accès aux fichiers et aux bases de données  
  
-   Sécurité d'accès du code  
  
-   Protection des ressources \(par exemple les journaux des événements, le Registre\)  
  
-   Stockage des informations confidentielles  
  
-   Vérification des entrées  
  
-   Passages des données aux technologies de script  
  
 Pour plus d'informations, consultez [Sécurisation des applications](../ide/securing-applications.md).  
  
## Extraits de code téléchargés  
 Les extraits de code IntelliSense installés par Visual Studio ne sont pas eux\-mêmes un risque de sécurité.  Toutefois, ils peuvent créer des problèmes de sécurité dans votre application.  Les extraits de code téléchargés à partir de Internet doivent être traités comme tout autre contenu téléchargé \(avec beaucoup de précaution.  
  
-   Les extraits de code de téléchargement uniquement des sites que vous faites confiance, et utilisent un logiciel anti\-virus à jour.  
  
-   Ouvrez tous les fichiers d'extrait de code téléchargés dans le Bloc\-notes ou dans l'éditeur XML de Visual Studio et examinez\-les avec soin avant de les installer.  Recherchez les problèmes suivants :  
  
    -   Code d'extrait de code peut endommager votre système si vous l'exécutez.  Lisez le code source avec soin avant de l'exécuter.  
  
    -   Le bloc d'aide d'URL du fichier d'extrait de code peut contenir des URL qui exécutent un fichier de script nuisible ou affiche un site Web offensif.  
  
    -   L'extrait de code peut contenir des références qui sont ajoutées de manière silencieuse à votre projet et peut être chargé n'importe où sur votre système.  Ces références ont pu être téléchargées sur votre ordinateur depuis l'emplacement où vous avez téléchargé l'extrait de code.  L'extrait de code peut ensuite appeler une méthode dans la référence qui exécute le code nuisible.  Pour vous protéger contre une telle attaque, examinez les blocs d'importations et de références du fichier d'extrait de code.  
  
## Voir aussi  
 [Visual Basic IntelliSense Code Snippets](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)   
 [Sécurisation des applications](../ide/securing-applications.md)   
 [Extraits de code](../ide/code-snippets.md)