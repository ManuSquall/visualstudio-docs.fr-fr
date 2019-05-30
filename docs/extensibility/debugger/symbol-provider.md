---
title: Fournisseur de symboles | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65debb8fcb41bec1d42c82654c26bc7d19c04a67
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348522"
---
# <a name="symbol-provider"></a>Fournisseur de symboles
Une implémentation d’évaluateur d’expression doit accéder aux informations symboliques de débogage générées par le compilateur de langage afin d’évaluer des variables et expressions. Il le fait en consommant les interfaces d’un fournisseur de symboles (SP), également appelé un gestionnaire de symboles.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit les Service Packs pour le code managé, ainsi que le code natif en utilisant le format de fichier de symboles de base de données de programme (PDB). Sauf s’il existe un fort besoin pour votre programme à utiliser des symboles stockés dans un format personnalisé, il est recommandé d’utiliser l’alimentation de secours fournie par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="implementation-notes"></a>Remarques d'implémentation
 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] moteurs de débogage s’attendre à communiquer avec les Service Packs à l’aide des interfaces du Common Language Runtime (CLR). Par conséquent, un Service Pack que vous allez travailler avec les moteurs de débogage de Visual Studio doit prendre en charge le CLR. Vous trouverez une liste complète des CLR toutes les interfaces de débogage dans debugref.doc, qui fait partie de la [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].

 Si votre fournisseur de services vous travaillerez uniquement avec votre moteur de débogage personnalisé, vous pouvez implémenter la procédure stockée comme vous le souhaitez selon les besoins de votre moteur de débogage.

## <a name="see-also"></a>Voir aussi
- [Composants du débogueur](../../extensibility/debugger/debugger-components.md)