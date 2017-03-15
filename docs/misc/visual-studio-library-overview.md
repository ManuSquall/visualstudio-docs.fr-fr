---
title: "Vue d’ensemble de la biblioth&#232;que Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Bibliothèque Visual Studio, vue d’ensemble"
ms.assetid: 48910975-7202-462f-a656-de67a4f8b14d
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Vue d’ensemble de la biblioth&#232;que Visual Studio
La bibliothèque Visual Studio est un ensemble de classes C\+\+ basées sur modèle pour simplifier la création de VSPackages en C\+\+ natif.  La bibliothèque de Visual Studio inclut le code source complet, comme jeu de fichiers d'en\-tête C\+\+.  les fichiers d'en\-tête sont installés dans *Chemin d'installation du kit de développement Visual Studio*\\VisualStudioIntegration \\Common\\Source\\CPP\\VSL\\Include \\.  
  
> [!NOTE]
>  La bibliothèque de Visual Studio s'appuie sur l'ATL \(ATL\) pour sa prise en charge des objets COM.  Pour plus d'informations, consultez [Introduction to ATL](/visual-cpp/atl/introduction-to-atl).  
  
 test unitaire de prises en charge de la bibliothèque de Visual Studio, pour son propre code et pour votre code.  Quelques tests unitaires sont inclus, comme suit :  
  
-   Les tests unitaires de bibliothèque Visual Studio sont installés dans *Chemin d'installation du kit de développement Visual Studio*\\VisualStudioIntegration\\Common\\Source\\CPP\\VSL\\UnitTest \\.  
  
-   Les classes de base pour les tests unitaires pour votre code sont dans *Chemin d'installation du kit de développement Visual Studio*\\VisualStudioIntegration\\Common\\Source\\CPP\\VSL\\Include\\VSLUnitTest .h.  
  
 Les implémentations fausses COM communément utilisé et des interfaces Visual Studio se trouvent dans les fichiers d'en\-tête, VSLMockSystemInterfaces.h et VSLMockVisualStudioInterfaces.h, qui sont installés dans *Chemin d'installation du kit de développement Visual Studio*\\VisualStudioIntegration\\Common\\Source\\CPP\\VSL\\Include \\.  
  
## Voir aussi  
 [Développement de VSPackages à l’aide de la bibliothèque Visual Studio](../misc/developing-vspackages-by-using-the-visual-studio-library.md)