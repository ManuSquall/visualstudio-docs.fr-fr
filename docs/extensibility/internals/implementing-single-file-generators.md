---
title: "Implémentation de générateurs de fichier unique | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b9fed2f4118600c48ad6cb769c8e697b06ae77d1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-single-file-generators"></a>Implémentation de générateurs de fichier unique
Un outil personnalisé, parfois appelé un générateur de fichier unique, peuvent être utilisées pour étendre la [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] et [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] dans les systèmes de projet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Un outil personnalisé est un composant COM qui implémente le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interface. À l’aide de cette interface, un outil personnalisé transforme un fichier d’entrée unique dans un fichier de sortie unique. Le résultat de la transformation peut être de code source, ou toute autre sortie qui est utile. Deux exemples de fichiers de code générés par un outil de personnalisés sont le code généré en réponse aux modifications dans un concepteur visuel et les fichiers générés à l’aide de Web Services Description Language (WSDL).  
  
 Lorsqu’un outil personnalisé est chargé, ou le fichier d’entrée est enregistré, le système de projet appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> (méthode) et passe une référence à un <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> interface de rappel, selon laquelle l’outil peut signaler sa progression à l’utilisateur.  
  
 Le fichier de sortie générés par l’outil personnalisé est ajouté au projet avec une dépendance sur le fichier d’entrée. Le système de projet détermine automatiquement le nom du fichier de sortie, en fonction de la chaîne retournée par l’implémentation de l’outil personnalisé de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.  
  
 Un outil personnalisé doit implémenter la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interface. Le cas échéant, des outils personnalisés prennent en charge la <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> interface pour récupérer des informations à partir des sources autres que le fichier d’entrée. Dans tous les cas, avant de pouvoir utiliser un outil personnalisé, vous devez l’inscrire avec le système ou dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Registre local. Pour plus d’informations sur l’inscription des outils personnalisés, consultez [l’inscription des générateurs de fichier unique](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exposition des types aux concepteurs visuels](../../extensibility/internals/exposing-types-to-visual-designers.md)