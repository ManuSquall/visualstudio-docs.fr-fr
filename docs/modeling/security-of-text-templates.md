---
title: Sécurité des modèles de texte
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eab987d406d6a2c05c8350aaac9dd1ecfc13e4a8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660088"
---
# <a name="security-of-text-templates"></a>Sécurité des modèles de texte
Les modèles de texte présentent les problèmes de sécurité suivants :

- Les modèles de texte sont vulnérables aux insertions de code arbitraires.

- Si le mécanisme utilisé par l’hôte pour rechercher un processeur de directive n’est pas sécurisé, un processeur de directive malveillant peut être exécuté.

## <a name="arbitrary-code"></a>Code arbitraire
 Lorsque vous écrivez un modèle, vous pouvez placer n’importe quel code dans les balises \< # # >. Cela permet d’exécuter du code arbitraire à partir d’un modèle de texte.

 Veillez à obtenir des modèles à partir de sources approuvées. Veillez à prévenir les utilisateurs finaux de votre application de ne pas exécuter les modèles qui ne proviennent pas de sources approuvées.

## <a name="malicious-directive-processor"></a>Processeur de directive malveillant
 Le moteur de modèle de texte interagit avec un hôte de transformation et un ou plusieurs processeurs de directive pour transformer le texte du modèle en fichier de sortie. Pour plus d’informations, consultez [processus de transformation de modèle de texte](../modeling/the-text-template-transformation-process.md).

 Si le mécanisme utilisé par l’hôte pour rechercher un processeur de directive n’est pas sécurisé, il risque d’exécuter un processeur de directive malveillant. Le processeur de directive malveillant peut fournir du code qui est exécuté en mode `FullTrust` lors de l’exécution du modèle. Si vous créez un hôte de transformation de modèle de texte personnalisé, vous devez utiliser un mécanisme sécurisé, tel que le registre, pour que le moteur localise les processeurs de directive.