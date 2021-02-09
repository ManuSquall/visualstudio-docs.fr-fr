---
title: Sécurité des modèles de texte
description: En savoir plus sur la sécurité et les modèles de texte, y compris des sujets tels que le code arbitraire et les processeurs de directive malveillants.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 11352eb33070d3401516948cc01c4b9bd7ab4f95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893319"
---
# <a name="security-of-text-templates"></a>Sécurité des modèles de texte
Les modèles de texte présentent les problèmes de sécurité suivants :

- Les modèles de texte sont vulnérables aux insertions de code arbitraires.

- Si le mécanisme utilisé par l’hôte pour rechercher un processeur de directive n’est pas sécurisé, un processeur de directive malveillant peut être exécuté.

## <a name="arbitrary-code"></a>Code arbitraire
 Lorsque vous écrivez un modèle, vous pouvez placer n’importe quel code dans les \<# #> balises. Cela permet d’exécuter du code arbitraire à partir d’un modèle de texte.

 Veillez à obtenir des modèles à partir de sources approuvées. Veillez à prévenir les utilisateurs finaux de votre application de ne pas exécuter les modèles qui ne proviennent pas de sources approuvées.

## <a name="malicious-directive-processor"></a>Processeur de directive malveillant
 Le moteur de modèle de texte interagit avec un hôte de transformation et un ou plusieurs processeurs de directive pour transformer le texte du modèle en fichier de sortie. Pour plus d’informations, consultez [processus de transformation de modèle de texte](../modeling/the-text-template-transformation-process.md).

 Si le mécanisme utilisé par l’hôte pour rechercher un processeur de directive n’est pas sécurisé, il risque d’exécuter un processeur de directive malveillant. Le processeur de directive malveillant peut fournir du code qui est exécuté en `FullTrust` mode lors de l’exécution du modèle. Si vous créez un hôte de transformation de modèle de texte personnalisé, vous devez utiliser un mécanisme sécurisé, tel que le registre, pour que le moteur localise les processeurs de directive.
