---
title: Common Language Runtime et évaluation de l’Expression | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 96f7da8da932fb535141712cc7725f1cfb120227
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49244944"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Common Language Runtime et évaluateur d’expression
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Compilateurs, tels que Visual Basic et c# (prononcé C-sharp), qui ciblent le Common Language Runtime (CLR), génèrent le langage MSIL (Microsoft Intermediate), qui est ultérieure compilés en code natif. Le CLR fournit un moteur de débogage (dé) pour déboguer le code résultant. Si vous envisagez d’intégrer votre langage de programmation propriétaire dans l’IDE Visual Studio, vous pouvez décider de compiler en langage MSIL et n’aurez donc pas à écrire votre propre DE. Toutefois, vous devrez écrire un évaluateur d’expression (EE) qui est capable de l’évaluation des expressions dans le contexte de votre langage de programmation.  
  
## <a name="discussion"></a>Discussion  
 Expressions de langage d’ordinateur sont généralement analysées pour produire un ensemble d’objets de données et un ensemble d’opérateurs utilisés pour les manipuler. Par exemple, l’expression « A + B » peut être analysée pour appliquer l’opérateur d’addition (+) pour les données des objets « A » et « B », ce qui peut provoquer dans un autre objet de données. L’ensemble des objets de données, d’opérateurs et leurs associations sont souvent représentées dans un programme sous forme d’arborescence, les opérateurs sur les nœuds de l’arborescence et les objets de données sur les branches. Une expression qui a été divisée en forme d’arborescence est souvent appelée une arborescence analysée.  
  
 Une fois qu’une expression a été analysée, un fournisseur de symboles (SP) est appelé pour évaluer chaque objet de données. Par exemple, si « A » est défini à la fois dans plus d’une méthode, puis la question « Qui A ? » doit répondre avant que la valeur de A peut être vérifiée. La réponse retournée par la procédure stockée est quelque chose comme « Le troisième élément sur le frame de pile cinquième » ou « A 50 octets au-delà du début de la mémoire statique alloués à cette méthode. »  
  
 Outre la production MSIL pour le programme lui-même, les compilateurs CLR peuvent également produire des informations de débogage très descriptives qui sont écrit dans un fichier de base de données de programme (.pdb). Tant qu’un compilateur de langage de propriétaires génère des informations de débogage dans le même format que les compilateurs CLR, Service Pack du CLR est en mesure d’identifier que de la langue nommé objets de données. Une fois qu’un objet de données nommée a été identifié, le EE utilise un objet de classeur pour associer (ou de la liaison) l’objet de données à la zone de mémoire qui contient la valeur de cet objet. Le DE peut ensuite obtenir ou définir une nouvelle valeur pour l’objet de données.  
  
 Un compilateur propriétaire peut fournir des informations de débogage en appelant CLR le `ISymbolWriter` interface (qui est défini dans le .NET Framework dans l’espace de noms `System.Diagnostics.SymbolStore`). Par la compilation en MSIL et l’écriture des informations de débogage via ces interfaces, un compilateur propriétaire peut utiliser le CLR Allemagne et le SP. Cela simplifie grandement l’intégration d’un langage propriétaire dans l’IDE Visual Studio.  
  
 Lorsque le DE CLR appelle le propriétaire EE pour évaluer une expression, l’Allemagne fournit le EE avec des interfaces pour un Service Pack et un objet de classeur. Par conséquent, écriture d’un moyen de moteur de débogage basé sur CLR qu’il est nécessaire uniquement pour implémenter les interfaces d’évaluateur d’expression appropriée ; le CLR prend en charge de la liaison et le symbole gérant pour vous.  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture d’un évaluateur d’expression de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

