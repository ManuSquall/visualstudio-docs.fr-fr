---
title: "Comment&#160;: modifier l&#39;espace de nom d&#39;un langage sp&#233;cifique &#224; un domaine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "langage spécifique à un domaine, espace de noms"
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 19
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 19
---
# Comment&#160;: modifier l&#39;espace de nom d&#39;un langage sp&#233;cifique &#224; un domaine
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez modifier l'espace de noms d'un langage spécifique au domaine.  Vous devez apporter la modification dans **Explorateur DÉSOLÉ**, dans les propriétés du projet de package DÉSOLÉ, et dans les informations de l'assembly.  
  
### Pour modifier l'espace de noms d'un langage spécifique au domaine  
  
1.  Dans **Explorateur DÉSOLÉ**, cliquez sur le nœud de **DÉSOLÉ** .  
  
2.  dans la fenêtre de **Propriétés** , modifiez la propriété d' **Espace de noms** .  
  
3.  Enregistrez la solution et transformez les modèles.  
  
4.  Dans le menu de **Projet** , cliquez sur **Propriétés DÉSOLÉ**.  
  
     Les propriétés de votre projet s'affichent.  
  
5.  Cliquez sur l'onglet **Application**.  
  
6.  Affectez à la propriété de **La cible par défaut l'espace de noms** au nouveau nom de l'espace de noms.  
  
7.  si vous souhaitez également modifier le nom de l'assembly, modifiez **Propriété nom de l'assembly.**  
  
8.  Si vous avez modifié le nom de l'assembly, DslPackage ouvert \\Package application et mettre à jour cette ligne :  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. Si vous avez écrit tout code personnalisé, veillez à modifier les références d'espace de noms et de classe dans les fichiers de code.  
  
10. réinitialisez l'instance expérimentale de Visual Studio.  
  
    1.  suppression **\\Users\\***{votre nom}***\\AppData\\Local\\Microsoft\\VisualStudio\\\*Exp**  
  
    2.  Dans le menu de **Démarrer** windows, choisissez **Tous les programmes**, **Microsoft Visual Studio 2010 SDK**, **Outils**, **réinitialisez l'instance expérimentale**.  
  
11. Dans le menu de **Générer** , choisissez **Régénérer la solution**.  
  
## Voir aussi  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/fr-fr/ca5e84cb-a315-465c-be24-76aa3df276aa)