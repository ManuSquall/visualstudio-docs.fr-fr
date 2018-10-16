---
title: Sécurité des modèles de texte | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, security
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 65b4b6616921dae0abb0bb54316d8b8262d1f652
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214680"
---
# <a name="security-of-text-templates"></a>Sécurité des modèles de texte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modèles de texte ont des problèmes de sécurité suivants :  
  
-   Modèles de texte sont vulnérables aux insertions de code arbitraire.  
  
-   Si le mécanisme que l’hôte utilise pour rechercher un processeur de directive n’est pas sécurisé, un processeur de directive malveillant peut être exécuté.  
  
## <a name="arbitrary-code"></a>Code arbitraire  
 Lorsque vous écrivez un modèle, vous pouvez placer n’importe quel code dans le \<## > balises. Cela permet à du code arbitraire à être exécutée à partir d’un modèle de texte.  
  
 Veillez à que vous procurer des modèles à partir de sources approuvées. Veillez à avertir les utilisateurs finaux de votre application d’exécuter les modèles qui ne proviennent pas de sources approuvées.  
  
## <a name="malicious-directive-processor"></a>Processeur de Directive malveillant  
 Le moteur de modèle de texte interagit avec un hôte de transformation et un ou plusieurs processeurs de directive pour transformer le texte du modèle dans un fichier de sortie. Pour plus d’informations, consultez [le processus de Transformation de modèle de texte](../modeling/the-text-template-transformation-process.md).  
  
 Si le mécanisme que l’hôte utilise pour rechercher un processeur de directive n’est pas sécurisé, elle s’exécute le risque d’exécution d’un processeur de directive malveillant. Le processeur de directive malveillant peut fournir du code qui est exécuté dans `FullTrust` mode lorsque le modèle est exécuté. Si vous créez un hôte de transformation de modèle de texte personnalisé, vous devez utiliser un mécanisme sécurisé, par exemple le Registre, le moteur de localiser des processeurs de directive.



