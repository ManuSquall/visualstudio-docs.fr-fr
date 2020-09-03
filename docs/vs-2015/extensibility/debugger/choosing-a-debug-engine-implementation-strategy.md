---
title: Choix d’une stratégie d’implémentation du moteur de débogage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6b03e69892da217d84d56b39b7df61784907d2b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183467"
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Choix d’une stratégie de mise en œuvre du moteur de débogage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Utilisez l’architecture Runtime pour déterminer la stratégie d’implémentation de votre moteur DE débogage (DE). Le moteur de débogage peut être créé dans le processus vers le programme à déboguer, dans le processus vers le gestionnaire de débogage de session Visual Studio (SDM), ou hors processus vers les deux. Les instructions suivantes doivent vous aider à choisir parmi ces trois stratégies.  
  
## <a name="guidelines"></a>Consignes  
 Bien qu’il soit possible que le soit hors processus vers le SDM et le programme à déboguer, il n’y a généralement aucune raison de le faire. Les appels entre les limites du processus sont relativement lents.  
  
 Les moteurs de débogage sont déjà fournis pour l’environnement Runtime natif Win32 et pour l’environnement common language runtime. Si vous devez remplacer le de pour l’un de ces environnements, vous devez créer le de in-process avec le SDM.  
  
 Dans le cas contraire, vous pouvez choisir entre créer le de in-process dans le SDM ou in-process pour le programme à déboguer. Il est important de déterminer si l’évaluateur d’expression de l’élément DE l’argument a besoin d’un accès fréquent au magasin de symboles de programme, et si le magasin de symboles peut être chargé en mémoire pour un accès rapide. Tenez également compte des éléments suivants :  
  
- S’il n’y a pas beaucoup d’appels entre l’évaluateur d’expression et le magasin de symboles, ou si le magasin de symboles peut être lu dans l’espace mémoire SDM, créez le de in-process dans le SDM. Vous devez retourner le CLSID du moteur de débogage au SDM lorsqu’il est attaché à votre programme. Le SDM utilise ce CLSID pour créer une instance in-process du de.  
  
- Si le DE doit appeler le programme pour accéder au magasin de symboles, créez le de in-process avec le programme. Dans ce cas, le programme crée l’instance de l’instance de.  
  
## <a name="see-also"></a>Voir aussi  
 [Extensibilité du débogueur de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
