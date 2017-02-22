---
title: "D&#233;tails du Runtime contr&#244;le source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôle de code source (Visual Studio SDK), détails de l'exécution"
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# D&#233;tails du Runtime contr&#244;le source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un projet est ajouté au contrôle de code source lorsque l'utilisateur ajoute un fichier dans le projet au contrôle de code source, ou via un contrôleur d'automation, tel qu'un Assistant.  Un projet ne spécifie pas pour lui\-même qu'il est sous contrôle de code source ; il prend en charge le contrôle de code source, mais doit lui ajouter manuellement.  
  
## S'inscrire dans un package de contrôle de code source  
 Lorsqu'un fichier dans votre projet est ajouté au contrôle de code source, l'environnement appelle l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> pour vous donner quatre chaînes opaques utilisées comme cookies par le système de contrôle de code source.  Stockez ces chaînes dans votre fichier projet.  Ces chaînes doivent être passées au stub de contrôle de code source \(le composant Visual Studio qui gère des ensembles de contrôle de code source\) au démarrage du type de projet par <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>appelant.  Cela ensuite charge le package approprié de contrôle de code source et transmet l'appel son implémentation d' `IVsSccManager2::RegisterSccProject`.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Prise en charge du contrôle de code Source](../../extensibility/internals/supporting-source-control.md)