---
title: Implémentation de générateurs de fichiers uniques | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2ca842f05692d5d47ed42470f58f2be0bb45007
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192688"
---
# <a name="implementing-single-file-generators"></a>Implémentation de générateurs de fichier unique
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un outil personnalisé (parfois appelé générateur de fichier unique) peut être utilisé pour étendre les [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] systèmes de projet et dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Un outil personnalisé est un composant COM qui implémente l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interface. À l’aide de cette interface, un outil personnalisé transforme un fichier d’entrée unique en un seul fichier de sortie. Le résultat de la transformation peut être du code source, ou toute autre sortie utile. Deux exemples de fichiers de code générés par un outil personnalisé sont générés par du code en réponse à des modifications dans un concepteur visuel et des fichiers générés à l’aide d’Web Services Description Language (WSDL).  
  
 Quand un outil personnalisé est chargé ou que le fichier d’entrée est enregistré, le système de projet appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> méthode et passe une référence à une <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> interface de rappel, ce qui permet à l’outil de signaler sa progression à l’utilisateur.  
  
 Le fichier de sortie généré par l’outil personnalisé est ajouté au projet avec une dépendance sur le fichier d’entrée. Le système de projet détermine automatiquement le nom du fichier de sortie, en fonction de la chaîne retournée par l’implémentation de l’outil personnalisé de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> .  
  
 Un outil personnalisé doit implémenter l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interface. Si vous le souhaitez, les outils personnalisés prennent en charge l' <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> interface pour récupérer des informations à partir de sources autres que le fichier d’entrée. Dans tous les cas, avant de pouvoir utiliser un outil personnalisé, vous devez l’inscrire auprès du système ou dans le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Registre local. Pour plus d’informations sur l’inscription des outils personnalisés, consultez [inscription de générateurs de fichiers uniques](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Détermination de l’espace de noms par défaut d’un projet](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Exposition des types aux concepteurs visuels](../../extensibility/internals/exposing-types-to-visual-designers.md)
