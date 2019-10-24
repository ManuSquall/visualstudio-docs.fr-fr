---
title: Implémentation de générateurs de fichiers uniques | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69bde665e62d063b6bab8784634777eeea02e941
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727174"
---
# <a name="implementing-single-file-generators"></a>Implémentation de générateurs de fichier unique
Un outil personnalisé (parfois appelé générateur de fichier unique) peut être utilisé pour étendre les systèmes de projet [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] et [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Un outil personnalisé est un composant COM qui implémente l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>. À l’aide de cette interface, un outil personnalisé transforme un fichier d’entrée unique en un seul fichier de sortie. Le résultat de la transformation peut être du code source, ou toute autre sortie utile. Deux exemples de fichiers de code générés par un outil personnalisé sont générés par du code en réponse à des modifications dans un concepteur visuel et des fichiers générés à l’aide d’Web Services Description Language (WSDL).

 Lorsqu’un outil personnalisé est chargé, ou que le fichier d’entrée est enregistré, le système de projet appelle la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> et passe une référence à une interface de rappel <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress>, qui permet à l’outil de signaler sa progression à l’utilisateur.

 Le fichier de sortie généré par l’outil personnalisé est ajouté au projet avec une dépendance sur le fichier d’entrée. Le système de projet détermine automatiquement le nom du fichier de sortie, en fonction de la chaîne retournée par l’implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> de l’outil personnalisé.

 Un outil personnalisé doit implémenter l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>. Si vous le souhaitez, les outils personnalisés prennent en charge l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> pour récupérer des informations à partir de sources autres que le fichier d’entrée. Dans tous les cas, avant de pouvoir utiliser un outil personnalisé, vous devez l’inscrire auprès du système ou dans le registre local [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Pour plus d’informations sur l’inscription des outils personnalisés, consultez [inscription de générateurs de fichiers uniques](../../extensibility/internals/registering-single-file-generators.md).

## <a name="see-also"></a>Voir aussi
- [Exposition des types aux concepteurs visuels](../../extensibility/internals/exposing-types-to-visual-designers.md)