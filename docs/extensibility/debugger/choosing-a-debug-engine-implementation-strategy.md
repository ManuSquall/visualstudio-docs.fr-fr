---
title: "Choix d&#39;une strat&#233;gie de mise en œuvre de moteur de d&#233;bogage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "moteurs de débogage, stratégies d'implémentation"
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# Choix d&#39;une strat&#233;gie de mise en œuvre de moteur de d&#233;bogage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilisez l'architecture au moment de l'exécution pour déterminer votre stratégie \(DE\) d'implémentation du moteur de débogage.  Le moteur de débogage peut être créé en cours de processus au programme à déboguer, in\-process au gestionnaire de débogage de session Visual Studio \(SDM\), ou hors processus à chacun d'eux.  Les indications suivantes doivent vous aider à choisir entre ces trois stratégies.  
  
## Indications  
 S'il est possible que le De soit out\-of\-process au SDM et au programme à déboguer, il n'y a généralement aucune raison pour ce faire.  Les appels au delà de les limites de processus sont relativement lente.  
  
 Les moteurs de débogage sont déjà fournis pour l'environnement d'exécution natif Win32 et pour l'environnement du common langage runtime.  Si vous devez remplacer " De " pour l'un ou l'autre de ces environnements, vous devez créer le De en cours de processus avec le SDM.  
  
 Sinon, vous pouvez choisir entre créer le De en cours de processus dans SDM ou in\-process au programme à déboguer.  Il est important de tenir compte si l'évaluateur d'expression du De a besoin d'accéder fréquemment utilisé au magasin de symboles de programme, et si le magasin de symboles peut être chargé en mémoire pour y accéder rapidement.  Considérez également les éléments suivants :  
  
-   S'il n'y a pas de nombreux appels entre l'évaluateur d'expression et le magasin de symboles, ou si le magasin de symboles peut être lu dans l'espace mémoire de SDM, créez le De en cours de processus dans SDM.  Vous devez retourner le CLSID du moteur de débogage vers SDM lorsqu'il est attaché à votre programme.  Le SDM utilise ce CLSID pour créer une instance in\-process du De.  
  
-   si le De doit appeler le programme pour accéder au magasin de symboles, créez le De in\-process avec le programme.  Dans ce cas, le programme crée l'instance de De.  
  
## Voir aussi  
 [Extensibilité du débogueur de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)