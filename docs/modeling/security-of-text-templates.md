---
title: Sécurité des modèles de texte | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 4acbe40d7229551e32f60d1503864b21840655be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="security-of-text-templates"></a>Sécurité des modèles de texte
Modèles de texte ont des problèmes de sécurité suivants :  
  
-   Modèles de texte sont vulnérables aux insertions de code arbitraire.  
  
-   Si le mécanisme que l’hôte utilise pour rechercher un processeur de directive n’est pas sécurisé, un processeur de directive malveillant peut être exécuté.  
  
## <a name="arbitrary-code"></a>Code arbitraire  
 Lorsque vous écrivez un modèle, vous pouvez placer n’importe quel code dans le \<## > balises. Cela permet au code arbitraire être exécutée à partir d’un modèle de texte.  
  
 Veillez à qu'obtenir les modèles à partir de sources fiables. Veillez à avertir les utilisateurs finaux de votre application d’exécuter des modèles qui ne proviennent pas de sources approuvées.  
  
## <a name="malicious-directive-processor"></a>Processeur de Directive malveillant  
 Le moteur de modèle de texte interagit avec un hôte de transformation et un ou plusieurs processeurs de directive pour transformer le texte du modèle à un fichier de sortie. Pour plus d’informations, consultez [le processus de Transformation de modèle de texte](../modeling/the-text-template-transformation-process.md).  
  
 Si le mécanisme que l’hôte utilise pour rechercher un processeur de directive n’est pas sécurisé, vous courez le risque d’un processeur de directive malveillant en cours d’exécution. Le processeur de directive malveillant peut fournir du code qui est exécuté dans `FullTrust` mode lorsque le modèle est exécuté. Si vous créez un hôte de transformation de modèle de texte personnalisé, vous devez utiliser un mécanisme sécurisé, tel que le Registre, le moteur de localiser des processeurs de directive.