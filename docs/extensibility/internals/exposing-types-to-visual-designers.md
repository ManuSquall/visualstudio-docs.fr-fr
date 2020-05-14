---
title: Exposer les types aux concepteurs visuels (fr) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708438"
---
# <a name="expose-types-to-visual-designers"></a>Exposer les types à des concepteurs visuels
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]doivent avoir accès à des définitions de classe et de type au moment de la conception afin d’afficher un concepteur visuel. Les classes sont chargées à partir d’un ensemble prédéfini d’assemblages qui comprennent l’ensemble complet de dépendance du projet actuel (références plus leurs dépendances). Il peut également être nécessaire pour les concepteurs visuels d’accéder aux classes et aux types qui sont définis dans les fichiers générés par des outils personnalisés.

 Les [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] systèmes et les systèmes de projet fournissent un soutien pour l’accès aux classes et aux types générés par le biais de fichiers portables temporaires exécutables (PE temporaires). Tout fichier généré par un outil personnalisé peut être compilé dans un assemblage temporaire afin que les types puissent être chargés à partir de ces assemblages et exposés à des concepteurs. La sortie de chaque outil personnalisé est compilée en un PE temporaire distinct, et le succès ou l’échec de cette compilation temporaire ne dépend que de la question de savoir si le fichier généré peut être compilé ou non. Même si un projet ne peut pas construire dans son ensemble, les PE temporaires individuels peuvent encore être disponibles pour les concepteurs.

 Le système de projet fournit un soutien complet pour le suivi des modifications au fichier de sortie d’un outil personnalisé, à condition que ces modifications soient le résultat de l’exécution de l’outil personnalisé. Chaque fois que l’outil personnalisé est exécuté, un nouveau PE temporaire est généré, et des notifications appropriées sont envoyées aux concepteurs.

> [!NOTE]
> Étant donné que le fichier de génération exécutable temporaire du programme se produit en arrière-plan, aucune erreur n’est signalée à l’utilisateur en cas d’échec de la compilation.

 Les outils personnalisés qui tirent parti du support temporaire PE doivent suivre les règles suivantes :

- **GeneratesDesignTimeSource** doit être réglé à 1 dans le registre.

     Aucune compilation de fichiers exécutable ne se déroule sans ce paramètre.

- Le code généré doit être dans la même langue que le paramètre de projet global.

     Le PE temporaire est compilé indépendamment de ce que <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> l’outil personnalisé indique que l’extension demandée à condition que **GeneratesDesignTimeSource** soit réglé à 1 dans le registre. L’extension n’a pas besoin d’être *.vb*, *.cs*, ou *.jsl*; il peut s’agir de n’importe quelle extension.

- Le code généré par l’outil personnalisé doit être valide, et il doit compiler seul <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> en utilisant uniquement l’ensemble des références présentes dans le projet au moment de l’exécution.

     Lorsqu’un PE temporaire est compilé, le seul fichier source fourni au compilateur est la sortie d’outil personnalisée. Par conséquent, un outil personnalisé qui utilise un PE temporaire doit générer des fichiers de sortie qui peuvent être compilés indépendamment des autres fichiers du projet.

## <a name="see-also"></a>Voir aussi
- [Introduction à l’objet BuildManager](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
- [Mettre en œuvre des générateurs à fichiers uniques](../../extensibility/internals/implementing-single-file-generators.md)
- [Enregistrez les générateurs à fichiers uniques](../../extensibility/internals/registering-single-file-generators.md)
