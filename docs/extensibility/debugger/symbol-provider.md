---
title: Fournisseur de symboles | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a98a5b80126bcb11109acedc2d24f226cde3714a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="symbol-provider"></a>Fournisseur de symbole
Une implémentation évaluateur d’expression doit accéder aux informations symboliques de débogage générées par le compilateur de langage afin d’évaluer les variables et les expressions. Il le fait en consommant les interfaces d’un fournisseur de symboles (SP), également appelé un gestionnaire de symboles.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Fournit des SPs pour le code managé, ainsi que le code natif en utilisant le format de fichier de symboles de base de données de programme (PDB). Sauf s’il existe un fort besoin pour votre programme afin d’utiliser des symboles stockés dans un format personnalisé, il est recommandé d’utiliser l’alimentation de secours fournie par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="implementation-notes"></a>Remarques d’implémentation  
 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] des moteurs de débogage s’attendre à communiquer avec l’alimentation de secours à l’aide des interfaces du Common Language Runtime (CLR). Par conséquent, un processeur travaillerez avec les moteurs de débogage de Visual Studio doit prendre en charge le CLR. Vous trouverez une liste complète de toutes les interfaces de débogage de CLR dans debugref.doc, qui fait partie de la [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].  
  
 Si votre processeur travaillerez uniquement avec votre moteur de débogage personnalisé, vous pouvez implémenter la procédure stockée comme vous le souhaitez selon les besoins de votre moteur de débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)