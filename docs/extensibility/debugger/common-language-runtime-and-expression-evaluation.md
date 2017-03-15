---
title: "Common Language Runtime et l’&#233;valuation d’Expression | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "évaluation de l’expression [Debugging SDK], le débogage"
  - "évaluation de l’expression et common language runtime"
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Common Language Runtime et l’&#233;valuation d’Expression
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Les compilateurs, tels que Visual Basic et c\# \(prononcé C\-sharp\), qui ciblent le Common Language Runtime \(CLR\), génèrent le langage MSIL \(Microsoft Intermediate\), qui est une version ultérieure compilées en code natif. Le CLR fournit un moteur de débogage \(DE\) pour déboguer le code résultant. Si vous prévoyez d’intégrer votre langage de programmation propriétaire dans l’IDE de Visual Studio, vous pouvez choisir de compiler en code MSIL et par conséquent inutile d’écrire votre propre DE. Toutefois, vous devrez écrire un évaluateur d’expression \(EE\) qui est capable de l’évaluation des expressions dans le contexte de votre langage de programmation.  
  
## Discussion  
 Les expressions de langage ordinateur sont analysées généralement pour produire un ensemble d’objets de données et un ensemble d’opérateurs utilisés pour les manipuler. Par exemple, l’expression « A \+ B » peut être analysée pour appliquer l’opérateur d’addition \(\+\) pour les données des objets « A » et « B », ce qui peut provoquer un autre objet de données. L’ensemble des objets de données, d’opérateurs et leurs associations sont souvent représentées dans un programme sous forme d’arborescence, avec les opérateurs sur les nœuds de l’arborescence et les objets de données sur les branches. Une expression qui a été divisée en forme d’arborescence est souvent appelée une arborescence analysée.  
  
 Une fois qu’une expression a été analysée, un fournisseur de symboles \(SP\) est appelé pour évaluer chaque objet de données. Par exemple, si « A » est définie à la fois dans plus d’une méthode, puis la question « Qui A ? » doit répondre avant que la valeur de A peut être établie. La réponse renvoyée par la procédure stockée est quelque chose comme « Le troisième élément dans le frame de pile cinquième » ou « A 50 octets au\-delà du début de la mémoire statique allouée à cette méthode ».  
  
 Outre la production MSIL pour le programme lui\-même, les compilateurs CLR peuvent également produire des informations de débogage très descriptives qui sont écrit dans un fichier de base de données de programme \(.pdb\). Tant qu’un compilateur de langage propriétaire génère des informations de débogage dans le même format que les compilateurs CLR, SP du CLR est en mesure d’identifier que du langage de nom des objets de données. Une fois qu’un objet de données a été identifié, le EE utilise un objet binder pour associer \(ou lier\) l’objet de données vers la zone de mémoire qui contient la valeur de cet objet. Le DE peut ensuite obtenir ou définir une nouvelle valeur pour l’objet de données.  
  
 Un compilateur propriétaire peut fournir des informations de débogage en appelant CLR le `ISymbolWriter` interface \(qui est défini dans le .NET Framework dans l’espace de noms `System.Diagnostics.SymbolStore`\). Par la compilation en MSIL et l’écriture des informations de débogage par ces interfaces, un compilateur propriétaire peut utiliser le CLR fr et SP. Ceci simplifie grandement l’intégration d’un langage propriétaire dans l’IDE de Visual Studio.  
  
 Lorsque la DE CLR appelle le propriétaire EE pour évaluer une expression, le DE fournit le EE avec des interfaces pour un processeur de stockage et un objet binder. Par conséquent, écrire un moyen de moteur de débogage basé sur CLR qu’il est uniquement nécessaire pour implémenter les interfaces évaluateur d’expression appropriée ; le CLR prend en charge de la liaison et le symbole de gestion pour vous.  
  
## Voir aussi  
 [Écriture d'un évaluateur d'Expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)