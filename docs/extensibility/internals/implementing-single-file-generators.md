---
title: Implémentation de Single-File Generator | Microsoft Docs
description: Découvrez comment utiliser un outil personnalisé qui implémente l’interface IVsSingleFileGenerator pour étendre des systèmes de projet Visual Basic et Visual C# dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 11ce8a69841d18d383e9d8e12c14d7af652d9cb8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900029"
---
# <a name="implementing-single-file-generators"></a>Implémentation de générateurs de fichier unique
Un outil personnalisé (parfois appelé générateur de fichier unique) peut être utilisé pour étendre les [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] systèmes de projet et dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Un outil personnalisé est un composant COM qui implémente l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interface. À l’aide de cette interface, un outil personnalisé transforme un fichier d’entrée unique en un seul fichier de sortie. Le résultat de la transformation peut être du code source, ou toute autre sortie utile. Deux exemples de fichiers de code générés par un outil personnalisé sont générés par du code en réponse à des modifications dans un concepteur visuel et des fichiers générés à l’aide d’Web Services Description Language (WSDL).

 Quand un outil personnalisé est chargé ou que le fichier d’entrée est enregistré, le système de projet appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> méthode et passe une référence à une <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> interface de rappel, ce qui permet à l’outil de signaler sa progression à l’utilisateur.

 Le fichier de sortie généré par l’outil personnalisé est ajouté au projet avec une dépendance sur le fichier d’entrée. Le système de projet détermine automatiquement le nom du fichier de sortie, en fonction de la chaîne retournée par l’implémentation de l’outil personnalisé de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> .

 Un outil personnalisé doit implémenter l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interface. Si vous le souhaitez, les outils personnalisés prennent en charge l' <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> interface pour récupérer des informations à partir de sources autres que le fichier d’entrée. Dans tous les cas, avant de pouvoir utiliser un outil personnalisé, vous devez l’inscrire auprès du système ou dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Registre local. Pour plus d’informations sur l’inscription des outils personnalisés, consultez [inscription de générateurs de fichiers uniques](../../extensibility/internals/registering-single-file-generators.md).

## <a name="see-also"></a>Voir aussi
- [Exposition des types aux concepteurs visuels](../../extensibility/internals/exposing-types-to-visual-designers.md)
