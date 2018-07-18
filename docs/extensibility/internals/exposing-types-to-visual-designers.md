---
title: Exposer des Types de concepteurs visuels | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 28dcc17c74a5b5ef3c9784fafe972beb6f170d90
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135972"
---
# <a name="exposing-types-to-visual-designers"></a>Exposer des Types de concepteurs visuels
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] doit avoir accès aux définitions de classe et le type au moment du design afin d’afficher un concepteur visuel. Les classes sont chargés à partir d’un ensemble prédéfini d’assemblys qui incluent le jeu complet de dépendance du projet actuel (références ainsi que leurs dépendances). Il peut également être nécessaire pour les concepteurs visuels pour accéder aux classes et les types qui sont définis dans les fichiers générés par des outils personnalisés.  
  
 Le [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] et [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] systèmes de projet prennent en charge pour l’accès aux classes générées et les types via portable temporaire des fichiers exécutables (PE temporaires). N’importe quel fichier généré par un outil personnalisé peut être compilé dans un assembly temporaire afin que les types peuvent être chargés à partir de ces assemblys et exposées aux concepteurs. La sortie de chaque outil personnalisé est compilée dans un PE temporaire distinct et la réussite ou l’échec de cette compilation temporaire dépend uniquement si le fichier généré peut être compilé. Même si un projet ne peut pas générer dans son ensemble, PE temporaires individuel peut rester disponible pour les concepteurs.  
  
 Le système de projet prend entièrement en charge pour le suivi des modifications apportées au fichier de sortie d’un outil personnalisé, à condition que ces modifications sont le résultat de l’exécution de l’outil personnalisé. Chaque fois que l’outil personnalisé est exécuté, un nouveau PE temporaire est généré et les notifications appropriées sont envoyées aux concepteurs.  
  
> [!NOTE]
>  Étant donné que le fichier exécutable de génération de programme temporaire se produit en arrière-plan, sans erreurs sont signalées à l’utilisateur si la compilation échoue.  
  
 Les outils personnalisés qui tirent parti de la prise en charge de PE temporaire doivent respecter les règles suivantes :  
  
-   `GeneratesDesignTimeSource` doit être définie sur 1 dans le Registre.  
  
     Aucune compilation fichier exécutable du programme n’a lieu sans ce paramètre.  
  
-   Le code généré doit être dans la même langue que le paramètre du projet global.  
  
     Le PE temporaire est compilé, quelle que soit ce que l’outil personnalisé qui signale que l’extension demandée dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> si `GeneratesDesignTimeSource` a la valeur 1 dans le Registre. L’extension ne doive pas être .vb, .cs ou .jsl ; Il peut être n’importe quelle extension.  
  
-   Le code généré par l’outil personnalisé doit être valide, et il doit se compiler sur son propre à l’aide de que l’ensemble de références présents dans le projet au moment <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> fin de l’exécution.  
  
     Lorsqu’un PE temporaire est compilé, le seul fichier source spécifié pour le compilateur est le résultat de l’outil personnalisé. Par conséquent, un outil personnalisé qui utilise un PE temporaire doit générer des fichiers de sortie qui peuvent être compilés indépendamment des autres fichiers dans le projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de l’objet BuildManager](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [Implémentation de générateurs de fichier unique](../../extensibility/internals/implementing-single-file-generators.md)   
 [Inscription de générateurs de fichier unique](../../extensibility/internals/registering-single-file-generators.md)