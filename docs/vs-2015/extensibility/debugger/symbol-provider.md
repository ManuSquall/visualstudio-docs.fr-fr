---
title: Fournisseur de symboles | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f09fbe350afff983bb5fefe880104201441430c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501827"
---
# <a name="symbol-provider"></a>Fournisseur de symboles
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [fournisseur de symboles](https://docs.microsoft.com/visualstudio/extensibility/debugger/symbol-provider).  
  
Une implémentation d’évaluateur d’expression doit accéder aux informations symboliques de débogage générées par le compilateur de langage afin d’évaluer des variables et expressions. Il le fait en consommant les interfaces d’un fournisseur de symboles (SP), également appelé un gestionnaire de symboles.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fournit les Service Packs pour le code managé, ainsi que le code natif en utilisant le format de fichier de symboles de base de données de programme (PDB). Sauf s’il existe un fort besoin pour votre programme à utiliser des symboles stockés dans un format personnalisé, il est recommandé d’utiliser l’alimentation de secours fournie par [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="implementation-notes"></a>Remarques d’implémentation  
 Le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] moteurs de débogage s’attendre à communiquer avec les Service Packs à l’aide des interfaces du Common Language Runtime (CLR). Par conséquent, un Service Pack que vous allez travailler avec les moteurs de débogage de Visual Studio doit prendre en charge le CLR. Vous trouverez une liste complète des CLR toutes les interfaces de débogage dans debugref.doc, qui fait partie de la [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)].  
  
 Si votre fournisseur de services vous travaillerez uniquement avec votre moteur de débogage personnalisé, vous pouvez implémenter la procédure stockée comme vous le souhaitez selon les besoins de votre moteur de débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)

