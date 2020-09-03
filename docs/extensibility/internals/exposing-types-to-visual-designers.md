---
title: Exposition de types aux concepteurs visuels | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9067f88b4bf1334e23a548bc6a2cbeb3eac6ad33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708438"
---
# <a name="expose-types-to-visual-designers"></a>Exposer des types à des concepteurs visuels
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] doit avoir accès aux définitions de classe et de type au moment du design pour afficher un concepteur visuel. Les classes sont chargées à partir d’un ensemble prédéfini d’assemblys qui incluent l’ensemble de dépendances complet du projet actuel (références et leurs dépendances). Il peut également être nécessaire pour les concepteurs visuels d’accéder aux classes et aux types définis dans les fichiers générés par les outils personnalisés.

 Les [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] systèmes de projet et fournissent la prise en charge de l’accès aux classes et aux types générés via des fichiers exécutables portables temporaires (PE temporaire). Tout fichier généré par un outil personnalisé peut être compilé dans un assembly temporaire afin que les types puissent être chargés à partir de ces assemblys et exposés aux concepteurs. La sortie de chaque outil personnalisé est compilée dans un fichier PE temporaire distinct, et la réussite ou l’échec de cette compilation temporaire dépend uniquement du fait que le fichier généré puisse ou non être compilé. Même si un projet peut ne pas être généré dans son ensemble, les PE temporaires individuels peuvent toujours être disponibles pour les concepteurs.

 Le système de projet offre une prise en charge complète du suivi des modifications apportées au fichier de sortie d’un outil personnalisé, à condition que ces modifications résultent de l’exécution de l’outil personnalisé. Chaque fois que l’outil personnalisé est exécuté, un nouveau PE temporaire est généré, et les notifications appropriées sont envoyées aux concepteurs.

> [!NOTE]
> Étant donné que le fichier temporaire de génération d’un exécutable de programme se produit en arrière-plan, aucune erreur n’est signalée à l’utilisateur si la compilation échoue.

 Les outils personnalisés qui tirent parti de la prise en charge temporaire du PE doivent respecter les règles suivantes :

- **GeneratesDesignTimeSource** doit avoir la valeur 1 dans le registre.

     Aucune compilation de fichier exécutable de programme n’a lieu sans ce paramètre.

- Le code généré doit être dans la même langue que le paramètre de projet global.

     Le PE temporaire est compilé indépendamment de ce que l’outil personnalisé signale comme l’extension demandée dans, à <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> condition que **GeneratesDesignTimeSource** soit défini sur 1 dans le registre. L’extension ne doit pas nécessairement être *. vb*, *. cs*ou *. jsl*; Il peut s’agir de n’importe quelle extension.

- Le code généré par l’outil personnalisé doit être valide et il doit être compilé seul en utilisant uniquement l’ensemble des références présentes dans le projet au moment de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> fin de l’exécution.

     Lorsqu’un PE temporaire est compilé, le seul fichier source fourni au compilateur est la sortie de l’outil personnalisé. Par conséquent, un outil personnalisé qui utilise un PE temporaire doit générer des fichiers de sortie qui peuvent être compilés indépendamment des autres fichiers dans le projet.

## <a name="see-also"></a>Voir aussi
- [Introduction à l’objet BuildManager](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
- [Implémenter des générateurs de fichiers uniques](../../extensibility/internals/implementing-single-file-generators.md)
- [Inscrire des générateurs de fichiers uniques](../../extensibility/internals/registering-single-file-generators.md)
