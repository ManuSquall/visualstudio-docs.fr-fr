---
title: Sécurité des modèles de texte
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 71052a0d4120a74269f2aa05412230284271e574
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
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