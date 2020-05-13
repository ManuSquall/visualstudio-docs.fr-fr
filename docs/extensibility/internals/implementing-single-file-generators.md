---
title: Mise en œuvre de générateurs à fichiers uniques (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e700d09277edbb04b30676d3965b6c996d0a11f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707656"
---
# <a name="implementing-single-file-generators"></a>Implémentation de générateurs de fichier unique
Un outil personnalisé - parfois appelé un générateur de fichiers [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] unique [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] - [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]peut être utilisé pour étendre les systèmes et les projets dans . Un outil personnalisé est un composant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> COM qui implémente l’interface. À l’aide de cette interface, un outil personnalisé transforme un fichier d’entrée unique en un seul fichier de sortie. Le résultat de la transformation peut être le code source, ou toute autre sortie qui est utile. Deux exemples de fichiers de code personnalisés générés par des outils sont le code généré en réponse aux modifications d’un concepteur visuel et des fichiers générés à l’aide du langage de description des services Web (WSDL).

 Lorsqu’un outil personnalisé est chargé ou que le fichier <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> d’entrée est enregistré, le système de projet appelle la méthode et transmet une référence à une <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> interface de rappel, par laquelle l’outil peut signaler ses progrès à l’utilisateur.

 Le fichier de sortie généré par l’outil personnalisé est ajouté au projet avec une dépendance au fichier d’entrée. Le système de projet détermine automatiquement le nom du fichier de sortie, en <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>fonction de la chaîne retournée par la mise en œuvre de l’outil personnalisé de .

 Un outil personnalisé <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> doit implémenter l’interface. En option, les <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> outils personnalisés prennent en charge l’interface pour récupérer des informations provenant de sources autres que le fichier d’entrée. Dans tous les cas, avant de pouvoir utiliser un outil personnalisé, vous devez l’enregistrer auprès du système ou dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registre local. Pour plus d’informations sur l’enregistrement des outils [personnalisés, voir l’enregistrement des générateurs de fichiers uniques](../../extensibility/internals/registering-single-file-generators.md).

## <a name="see-also"></a>Voir aussi
- [Exposition des types aux concepteurs visuels](../../extensibility/internals/exposing-types-to-visual-designers.md)
