---
title: Common Language Runtime et évaluation de l’Expression | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 370b7963c71b74674c7d323a5fa1c2650d3f08d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Common Language Runtime et évaluation d’Expression
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Compilateurs, tels que Visual Basic et c# (prononcé C-sharp), qui ciblent le Common Language Runtime (CLR), génèrent le langage MSIL (Microsoft Intermediate), qui est ultérieure compilées en code natif. Le CLR fournit un moteur de débogage (DE) pour déboguer le code résultant. Si vous prévoyez d’intégrer votre langage de programmation propriétaire de l’IDE de Visual Studio, vous pouvez décider de compiler en langage MSIL et par conséquent inutile d’écrire votre propre DE. Toutefois, vous devrez écrire un évaluateur d’expression (EE) qui est capable de l’évaluation des expressions dans le contexte de votre langage de programmation.  
  
## <a name="discussion"></a>Discussion  
 Les expressions de langage ordinateur sont généralement analysées pour générer un ensemble d’objets de données et un ensemble d’opérateurs utilisés pour les manipuler. Par exemple, l’expression « A + B » peut être analysée pour appliquer l’opérateur d’addition (+) pour les données des objets « A » et « B », ce qui peut provoquer un autre objet de données. L’ensemble des objets de données, d’opérateurs et leurs associations sont souvent représentées dans un programme sous forme d’arborescence, avec les opérateurs sur les nœuds de l’arborescence et les objets de données sur les branches. Une expression qui a été divisée en forme d’arborescence est souvent appelée une arborescence analysée.  
  
 Une fois qu’une expression a été analysée, un fournisseur de symboles (SP) est appelé pour évaluer chaque objet de données. Par exemple, si « A » est défini à la fois de plus d’une méthode, puis la question « Quel A ? » doit répondre avant que la valeur de A peut être établie. La réponse renvoyée par la procédure stockée est un nom tel que « Le troisième élément sur le frame de pile cinquième » ou « A qui est au-delà du début de la mémoire statique de 50 octets alloués à cette méthode. »  
  
 En plus de la production MSIL pour le programme lui-même, les compilateurs CLR peuvent également produire des informations de débogage très descriptives qui sont écrit dans un fichier de base de données de programme (.pdb). Tant qu’un compilateur de langage de propriétaires génère des informations de débogage dans le même format que les compilateurs CLR, SP du CLR est en mesure d’identifier que du langage de nom des objets de données. Une fois qu’un objet de données nommé a été identifié, le EE utilise un objet binder associer (ou lier) de l’objet de données à la zone de mémoire qui contient la valeur de cet objet. Le DE peut ensuite obtenir ou définir une nouvelle valeur pour l’objet de données.  
  
 Un compilateur propriétaire peut fournir des informations de débogage en appelant CLR le `ISymbolWriter` interface (qui est défini dans le .NET Framework dans l’espace de noms `System.Diagnostics.SymbolStore`). Par la compilation en langage MSIL et l’écriture des informations de débogage via ces interfaces, un compilateur propriétaire peut utiliser le DE CLR et d’un fournisseur de services. Cela simplifie grandement l’intégration d’un langage propriétaire dans l’IDE de Visual Studio.  
  
 Lorsque le DE CLR appelle le propriétaire EE pour évaluer une expression, le DE fournit le EE avec des interfaces pour un processeur de stockage et un objet de classeur. Par conséquent, l’écriture d’un moyen de moteur de débogage de basé sur CLR qu’il est uniquement nécessaire pour implémenter les interfaces évaluateur d’expression appropriée ; le CLR prend en charge de la liaison et le symbole de gestion pour vous.  
  
## <a name="see-also"></a>Voir aussi  
 [L’écriture d’un évaluateur d’Expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)