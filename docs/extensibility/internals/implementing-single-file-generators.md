---
title: Implémentation de générateurs de fichier unique | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce8bca614d0af9c7b0557d5b5979797f127a47af
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62860367"
---
# <a name="implementing-single-file-generators"></a>Implémentation de générateurs de fichier unique
Un outil personnalisé, parfois appelé un générateur de fichier unique, peuvent être utilisées pour étendre la [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] et [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] dans les systèmes de projet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Un outil personnalisé est un composant COM qui implémente le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interface. À l’aide de cette interface, un outil personnalisé transforme un fichier d’entrée unique dans un fichier de sortie unique. Le résultat de la transformation peut être le code source, ou toute autre sortie qui est utile. Deux exemples de fichiers de code générés par un outil personnalisé de code sont généré en réponse aux modifications dans un concepteur visuel et les fichiers générés à l’aide de Web Services Description Language (WSDL).

 Lorsqu’un outil personnalisé est chargé, ou le fichier d’entrée est enregistré, le système de projet appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> (méthode) et passe une référence à un <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> interface de rappel, par laquelle l’outil peut signaler sa progression à l’utilisateur.

 Le fichier de sortie qui génère l’outil personnalisé est ajouté au projet avec une dépendance sur le fichier d’entrée. Le système de projet détermine automatiquement le nom du fichier de sortie, en fonction de la chaîne retournée par l’implémentation de l’outil personnalisé de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.

 Un outil personnalisé doit implémenter la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interface. Si vous le souhaitez, des outils personnalisés prennent en charge la <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> interface pour récupérer des informations à partir de sources autres que le fichier d’entrée. Dans tous les cas, avant de pouvoir utiliser un outil personnalisé, vous devez l’inscrire avec le système ou dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Registre local. Pour plus d’informations sur l’inscription des outils personnalisés, consultez [l’inscription de générateurs de fichier unique](../../extensibility/internals/registering-single-file-generators.md).

## <a name="see-also"></a>Voir aussi
- [Exposition des types aux concepteurs visuels](../../extensibility/internals/exposing-types-to-visual-designers.md)