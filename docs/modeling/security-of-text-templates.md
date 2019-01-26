---
title: Sécurité des modèles de texte
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 94b2520ffafe3e99420bf77577b59341b6d216aa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957206"
---
# <a name="security-of-text-templates"></a>Sécurité des modèles de texte
Modèles de texte ont des problèmes de sécurité suivants :

-   Modèles de texte sont vulnérables aux insertions de code arbitraire.

-   Si le mécanisme que l’hôte utilise pour rechercher un processeur de directive n’est pas sécurisé, un processeur de directive malveillant peut être exécuté.

## <a name="arbitrary-code"></a>Code arbitraire
 Lorsque vous écrivez un modèle, vous pouvez placer n’importe quel code dans le \<## > balises. Cela permet à du code arbitraire à être exécutée à partir d’un modèle de texte.

 Veillez à que vous procurer des modèles à partir de sources approuvées. Veillez à avertir les utilisateurs finaux de votre application d’exécuter les modèles qui ne proviennent pas de sources approuvées.

## <a name="malicious-directive-processor"></a>Processeur de Directive malveillant
 Le moteur de modèle de texte interagit avec un hôte de transformation et un ou plusieurs processeurs de directive pour transformer le texte du modèle dans un fichier de sortie. Pour plus d’informations, consultez [le processus de Transformation de modèle de texte](../modeling/the-text-template-transformation-process.md).

 Si le mécanisme que l’hôte utilise pour rechercher un processeur de directive n’est pas sécurisé, elle s’exécute le risque d’exécution d’un processeur de directive malveillant. Le processeur de directive malveillant peut fournir du code qui est exécuté dans `FullTrust` mode lorsque le modèle est exécuté. Si vous créez un hôte de transformation de modèle de texte personnalisé, vous devez utiliser un mécanisme sécurisé, par exemple le Registre, le moteur de localiser des processeurs de directive.