---
title: Prise en charge d’Automation pour les Pages Options | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7cb2634f5a16c62222cf360065cae0c22aef6667
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948875"
---
# <a name="automation-support-for-options-pages"></a>Prise en charge de l’automatisation pour les pages Options
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackages peut fournir une personnalisée **Options** boîtes de dialogue pour le **outils** menu (pages d’Options Outils) dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et vous pouvez les rendre disponibles pour le modèle automation.  
  
## <a name="tools-options-pages"></a>Pages d’Options Outils  
 Pour créer un **Outils/Options** page, un VSPackage doit fournir une implémentation de contrôle utilisateur retournée à l’environnement via l’implémentation du VSPackage de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> (méthode), (ou pour le code managé du <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> méthode).  
  
 Il est facultatif, mais il est vivement recommandé d’autoriser l’accès à cette nouvelle page via le modèle automation. Pour cela, les étapes suivantes :  
  
1. Étendre la <xref:EnvDTE._DTE.Properties%2A> objet via l’implémentation d’un objet dérivé de IDispatch.  
  
2. Retourner une implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> (méthode) (ou pour le code managé le <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> méthode) à l’objet dérivé de IDispatch.  
  
3. Lorsqu’un utilisateur d’automation appelle le <xref:EnvDTE._DTE.Properties%2A> méthode sur un personnalisé **Option** page de propriétés, l’environnement utilise le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> méthode pour obtenir un personnalisé **Outils/Options** automation de la page mise en œuvre.  
  
4. L’objet automation du VSPackage est ensuite utilisé pour fournir chacune <xref:EnvDTE.Property> retourné par <xref:EnvDTE._DTE.Properties%2A>.  
  
   Pour un exemple d’implémentation d’une page Outils/Options personnalisée, consultez [exemples d’extensibilité Visual Studio](../../misc/vssdk-samples.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exposition des objets de projet](../../extensibility/internals/exposing-project-objects.md)
